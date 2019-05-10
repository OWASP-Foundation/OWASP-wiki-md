## Overview

This is a filter to block XSS attacks on pdf files, as originally
discovered by [Stefano Di Paola and Giorgio
Fedon](http://www.wisec.it/vulns.php?page=9), served by Apache with
[mod_rewrite](http://httpd.apache.org/docs/1.3/mod/mod_rewrite.html)
installed. After developing an initial implementation, I found it to be
almost identical to an [algorithm developed by Amit
Klein](http://www.securityfocus.com/archive/1/456294/30/0/threaded).
After further inspection, I was able to optimize the algorithm even more
as explained below.

So far I've seen two real-world implementations of this algorithm. One
[for Java EE](PDF_Attack_Filter_for_Java_EE "wikilink") right here in
OWASP and a second one developed by F5
[iRules](http://devcentral.f5.com/Default.aspx?tabid=29&articleType=ArticleView&articleID=70).

Adobe has published their official [server-side
workarounds](http://www.adobe.com/support/security/advisories/apsa07-02.html).
The Adobe solutions work by changing either the
[Content-Type](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.17)
or [Content-Disposition](http://www.ietf.org/rfc/rfc2183.txt) headers in
order to force the pdf to be downloaded avoiding the Adobe plug-in. I
think the "Content-Type" change is less desirable as I've seen it
working improperly in some cases. The downside of either implementation
is that for long-established commercial websites, this changes the
effective functionality of the site in that pdf's (on PC's configured
with Adobe plug in), no longer open up in the browser.

Ideally, in order not to lose the functionality, we can clear the
"anchor/fragment" off of the original URL by forcing a redirect to an
URL containing a "hard to reproduce" but verifiable token in the query
string (or even in the location).

More details of the attack are discussed
[elsewhere](http://www.gnucitizen.org/blog/danger-danger-danger). The
software in the public domain to make it easy for anyone to use for any
purpose.

## References

1.  [PDF Attack Filter for Java
    EE](PDF_Attack_Filter_for_Java_EE "wikilink") entry for structure
    and skeleton contents.
2.  [Algorithm](http://www.securityfocus.com/archive/1/456294/30/0/threaded)
    developed by Amit Klein.
3.  [Base64 code](http://www.samba.org/ftp/unpacked/junkcode/base64.c).
4.  [OpenSSL encryption
    code.](http://www.faqs.org/docs/gazette/encryption.html) Vinayak
    Hegde.
5.  [Adobe Acrobat Reader Plugin - Multiple
    Vulnerabilities](http://www.wisec.it/vulns.php?page=9). Stefano Di
    Paola
6.  [Server-side
    workarounds](http://www.adobe.com/support/security/advisories/apsa07-02.html).
    Adobe

## Approach

My initial approach was almost the same as the
[approach](PDF_Attack_Filter_for_Java_EE#Approach "wikilink") described
for the Java EE implementation. The main difference was that in the case
that a request arrives with a query string, but one which doesn't match
our generated token, instead of setting the Content-Disposition and
forcing a download of the file, we redirect to the same URL containing a
newly generated token in the query string.

On further study, I simplified the approach, hopefully maintaining the
same level of security. This consists of at most a single rewrite based
on two conditions, the file is a pdf and it has a correctly generated
token in the query string. If the two conditions are not met, we
redirect to the same pdf but with a valid token in the query string.
This method skips step 2 and 3 of the *Ami* algorithm. Purposefully the
query string is cleared out on the redirect and only the token is
passed. The reason is to avoid possible other hacks playing around with
the query string. Unless the pdf is dynamically created and depends on
get parameters, this shouldn't be a problem. Certainly it is possible to
implement a version of rewrite rules which will allow us also to
maintain the original query string, without difficulty.

## Methods

### Apache mod_rewrite rules

```
    RewriteEngine   On
    RewriteLog "logs/rewrite.log"
    RewriteLogLevel 10

    RewriteMap tokenize prg:/home/jon/tokenize


        RewriteCond %{REQUEST_URI} .pdf
        RewriteCond ${tokenize:%{REMOTE_ADDR}%{QUERY_STRING}} !^$
        RewriteRule ^(.*)$ $1?${tokenize:%{REMOTE_ADDR}} [R,L]
```

The first rewrite condition matches all pdf files. The second condition
matches all requests whose query string doesn't match our generated
token, which is created by passing the client IP address
*%{REMOTE_ADDR}* and the query string supplied in the request
*%{QUERY_STRING}*.

Assuming we are requesting a pdf file, there are different cases that
the second part of this rule handles.

1.  First time request without any query string, e.g.
        http://www.aaa.com/test.pdf
    tokenize is called with the client ip address (the query string is
    empty), e.g.
        "192.168.0.1"
    and returns a new token
        "TOKENDELIMITERRMoa43/zBdWp+E474FkoOkgJ2ZKNds6N"
    As the value is not zero, we send back a redirect to
        http://www.aaa.com/test.pdf?TOKENDELIMITERRMoa43/zBdWp+E474FkoOkgJ2ZKNds6N
2.  Request comes with a valid token, such as:
        http://www.aaa.com/test.pdf?TOKENDELIMITERRMoa43/zBdWp+E474FkoOkgJ2ZKNds6N
    tokenize is called with just client ip address and query string,
    e.g.
        "192.168.0.1TOKENDELIMITERRMoa43/zBdWp+E474FkoOkgJ2ZKNds6N"
    and tokenize will return an empty string. At this point the second
    RewriteCond will fail and the request will pass through to normal
    Apache processing.
3.  Request comes in with a query string or an invalid token, such as:
        http://www.aaa.com/test.pdf?TOKENDELIMITERfaketokeninventedbyhacker
    or
        http://www.aaa.com/test.pdf?x=1&b=2
    In this case, tokenize will be passed client ip address and query
    string, for example:
        "192.168.0.1TOKENDELIMITERfaketokeninventedbyhacker"
    and the return value will be the correct token
        "192.168.0.1TOKENDELIMITERRMoa43/zBdWp+E474FkoOkgJ2ZKNds6N"
    RewriteCond will evaluate true and we will perform the redirect as
    in the first case.

### Apache mod_rewrite rules - *Amit* version

Here is a previous version of rewrite rules, using the same tokenize,
much more similar to Amit's algorithm even if I think that it changes
nothing in respect to the actual functionality.

```
    RewriteEngine   On
    RewriteLog "logs/rewrite.log"
    RewriteLogLevel 10

    RewriteMap tokenize prg:/home/jon/tokenize

    RewriteCond %{REQUEST_URI} .pdf
    RewriteCond %{QUERY_STRING} ^$
    RewriteRule ^(.*)$ $1?${tokenize:%{REMOTE_ADDR}} [R,L]

    RewriteCond %{REQUEST_URI} .pdf
    RewriteRule ^(.*)$ $1?${tokenize:%{REMOTE_ADDR}%{QUERY_STRING}}

    RewriteCond %{REQUEST_URI} .pdf
    RewriteCond %{QUERY_STRING} !^$
    RewriteRule ^(.*)$ $1?${tokenize:%{REMOTE_ADDR}} [R,L]
```

### tokenize - *mod_rewrite* prg

Now on to "tokenize". This is a mod_rewrite
[RewriteMap](http://httpd.apache.org/docs/1.3/mod/mod_rewrite.html#RewriteMap)
external program. It is run on initialization of the rewrite engine and
loops on stdin where it receives text to transform, delimited by
newlines. Output is on stdout, terminated by newline. Our version of
tokenize interprets the input text as two pieces, some client-based
info, such as client-ip or other, and a possible token to check, for
example

```
          192.168.0.1TOKENDELIMITERRMoa43/zBdWp+E474FkoOkgJ2ZKNds6N
```

Tokenize will generate a token using all of the text before
"TOKENDELIMITER" + any extra info such as current time (maybe taking out
minutes). If the token generated matches the stuff after
"TOKENDELIMITER" it will write a blank line on stdout, otherwise it will
write out the new token on stdout, e.g.

```
    TOKENDELIMITERRMoa43/zBdWp+E474FkoOkgJ2ZKNds6N
```

#### "C" source code

This code has been only minimally tested. Please help verify the
approach and the implementation used here.

Note: In order to use, you must fill in key and initial value (key &
iv), and of course these should be kept secret. Also you may want to
modify how time/date are used as well as any other system variables you
might want to add in.

    /**
     *
     *  This software is in the public domain with no warranty.
     *
     * @author     Jon Zaid
     * @created    January 14, 2007
     */

    #include <time.h>
    #include <openssl/blowfish.h>
    #include <openssl/evp.h>
    #include <openssl/blowfish.h>
    #include <openssl/evp.h>
    #include <fcntl.h>
    #include <stdio.h>
    #include <sys/stat.h>
    #include <sys/types.h>

    #define IP_SIZE 1024
    #define OP_SIZE 1032
    #include <stdio.h>

    #include <string.h>
    #include <errno.h>
    #include <stdlib.h>


    #define TOKEN_EXPIRY_TIME 120

    /***************************************************************************
    encode a buffer using base64 - simple and slow algorithm. null terminates
    the result.
    Code taken from http://www.samba.org/ftp/unpacked/junkcode/base64.c
      ***************************************************************************/
    static void base64_encode(char *buf, int len, char *out)
    {
        char *b64 = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/";
        int bit_offset, byte_offset, idx, i;
        unsigned char *d = (unsigned char *)buf;
        int bytes = (len*8 + 5)/6;

        memset(out, 0, bytes+1);

        for (i=0;i<bytes;i++) {
            byte_offset = (i*6)/8;
            bit_offset = (i*6)%8;
            if (bit_offset < 3) {
                idx = (d[byte_offset] >> (2-bit_offset)) & 0x3F;
            } else {
                idx = (d[byte_offset] << (bit_offset-2)) & 0x3F;
                if (byte_offset+1 < len) {
                    idx |= (d[byte_offset+1] >> (8-(bit_offset-2)));
                }
            }
            out[i] = b64[idx];
        }
    }



    unsigned char key[16] = { xx, xx, xx, xx, xx, xx, xx, xx, xx, xx, xx, xx, xx, xx, xx, xx};
    unsigned char iv[8] = {xx, xx, xx, xx, xx, xx, xx, xx};


    /* code taken from
    http://www.faqs.org/docs/gazette/encryption.html
    */

    int
    encrypt_str (char *in, char *out)
    {
        int olen, tlen, n;
        char outbuf[IP_SIZE];
        EVP_CIPHER_CTX ctx;
        EVP_CIPHER_CTX_init (&ctx);
        EVP_EncryptInit (&ctx, EVP_bf_cbc (), key, iv);

        if (EVP_EncryptUpdate (&ctx, outbuf, &olen, in, strlen(in)) != 1)
            {
            printf ("error in encrypt update\n");
            return 0;
            }

        if (EVP_EncryptFinal (&ctx, outbuf + olen, &tlen) != 1)
            {
            printf ("error in encrypt final\n");
            return 0;
            }
        olen += tlen;
        base64_encode(outbuf, olen, out);

        EVP_CIPHER_CTX_cleanup (&ctx);
        return 1;
    }




    #define MAX_TOKEN_LEN   1024
    #define TOKEN_PATTERN   "TOKENDELIMITER"
    /* in contains the request buffer which is an arbitrary string possibly
       followed by a delimited token (delimted "TOKEN")
       we use the time as well as the string up to TOKEN to delimit it
    */
    void
    gen_token(char *in, char *token64, int token64_len)
    {
    time_t now;
    char token[MAX_TOKEN_LEN];
    int len;
    char *pToken;

        /* copy first part of buffer to token */
        if (pToken = strstr(in, TOKEN_PATTERN))
            len = pToken - in;
        else
            len = strlen(in);
        if (len >= MAX_TOKEN_LEN)
            len = MAX_TOKEN_LEN-1;
        strncpy(token, in, len);
        token[len] = '\0';

        /* now add time to it */
        now = time(NULL);
        now =  now - (now % TOKEN_EXPIRY_TIME);
        snprintf(&token[len], sizeof(token)-len-1, "%d",  now);
        encrypt_str(token, token64);
    }


    /*
    mod_rewrite prg handler
    Requests arrive on stdin delimter by \n
    Single line reply for every request

    Algorithim:
        generate a token based on input buffer contents and any other sysinfo
        we want;
        if request buffer already contains a token compare it with the
        generated one;
        is (generated same as passed token)
            return emptyline;
        else
            return generated token;
    */

    main()
    {

        while (1)
        { /* for all requests */
        char reqBuffer[4096];
        char c;
        int len;
        int charsRead;
        char token64[MAX_TOKEN_LEN*2];
        char *pToken = reqBuffer;

        len = 0;

        while (    ((charsRead = read(0, &c, 1)) == 1)
            && (len < sizeof(reqBuffer)-2))
            {
            if (c == '\n') /* end of single request? */
            break;
            reqBuffer[len++] = c;
            }
        if (charsRead < 0) break; /* exiting from prg/apache? */
        reqBuffer[len] = '\0';

        /* based on contents of request, generate a string token. Must be
           zero-delimted and ASCII printable chars, e.g. base64 */
        gen_token(reqBuffer, token64, sizeof(token64));

        /* find pointer to starting of actual encrypted token in
           request buffer, e.g.
            xxxxxxxxxxxxxxxxTOKENencryptedtoken
           we will point to "encryptedtoken".
        */
        if (pToken = strstr(reqBuffer, TOKEN_PATTERN))
            pToken += strlen(TOKEN_PATTERN);

        /* compare newly generated token with one that is passed
           and if not same output the newly generated token, else
           don't output anything */
        if (!pToken || strcmp(token64, pToken))
            {
            printf("%s %s\n", token64, pToken?pToken:"NULL");
            write(1, TOKEN_PATTERN, strlen(TOKEN_PATTERN));
            write(1, token64, strlen(token64));
            }
        write(1, "\n", 1);
        } /* for all requests */
    }

[Category:How To](Category:How_To "wikilink")
[Category:OWASP_Validation_Project](Category:OWASP_Validation_Project "wikilink")
[Category:Control](Category:Control "wikilink")
[Category:FixME/old](Category:FixME/old "wikilink")