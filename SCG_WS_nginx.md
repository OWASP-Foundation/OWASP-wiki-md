NginX Secure Configuration Guide

## Summary

This provides NginX security configuration harden guide. The
configuration guide is focused on the NginX itself. Therefore, the Linux
OS configuration hardening is not covered here.

It includes the following topic: 2.1 Buffer Overflow Protection 2.2
Remove Unnecessary backup files 2.3 Remove Version number 2.4 Mitigating
Slow HTTP DoS Attack 2.5 Allow Access To Specified Domain Only 2.6 Limit
IP clients access 2.7 SSL/TLS Configuration 2.8 SSL Module 2.9 HTTP
secure Header 2.10 Limit HTTP Method

## Secure Configuration

### Buffer Overflow Protection

```
 ## Size Limits & Buffer Overflows
 ## the size may be configured based on the needs.
  client_body_buffer_size  100K;
  client_header_buffer_size 1k;
  client_max_body_size 100k;
  large_client_header_buffers 2 1k;
```

Refer here for detailed of each configuration value.
<http://nginx.org/en/docs/http/ngx_http_core_module.html>

Based on CIS Appache configuration guide

  - Limit the size of Http request header to 1024 bytes or less
  - Limits the number of bytes that are allowed in a request body to
    102400 or les

### Remove Unnecessary backup files

Use the following command to search if there is any unnecessary backup
files to be removed.

    # find /nginx -name '.?*' -not -name .ht* -or -name '*~' -or -name '*.bak*' -or -name '*.old*'
    # find /usr/local/nginx/html/ -name '.?*' -not -name .ht* -or -name '*~' -or -name '*.bak*' -or -name '*.old*'

### Remove Version number

    # Display nginx Version number in error or http header may result in hacker to search for known vulnerability.
    # Therefore, the version number should be removed for every http response.
    server_tokens off;

### Mitigating Slow HTTP DoS Attack

```
 ## Timeouts definition ##
  client_body_timeout   10;
  client_header_timeout 10;
  keepalive_timeout     5 5;
  send_timeout          10;
 ## End ##
```

  - client_body_timeout: Defines a timeout for reading client request
    body. The timeout is set only for a period between two successive
    read operations, not for the transmission of the whole request body.
    If a client does not transmit anything within this time, the 408
    (Request Time-out) error is returned to the client.
  - client_header_timeout: Defines a timeout for reading client
    request header. If a client does not transmit the entire header
    within this time, the 408 (Request Time-out) error is returned to
    the client.
  - keepalive_timeout: The first parameter sets a timeout during which
    a keep-alive client connection will stay open on the server side.
    The zero value disables keep-alive client connections. The optional
    second parameter sets a value in the “Keep-Alive: timeout=time”
    response header field. Two parameters may differ. The “Keep-Alive:
    timeout=time” header field is recognized by Mozilla and Konqueror.
    MSIE closes keep-alive connections by itself in about 60 seconds.
  - send_timeout: Sets a timeout for transmitting a response to the
    client. The timeout is set only between two successive write
    operations, not for the transmission of the whole response. If the
    client does not receive anything within this time, the connection is
    closed.

Refer here for detailed of each configuration value.
<http://nginx.org/en/docs/http/ngx_http_core_module.html>

### Allow Access To Specified Domain Only

    ##  i.e. abc.com, images.abc.com and www.abc.com
          if ($host !~ ^(abc.com
    |www.abc.com
    |images.abc.com)$ ) {
             return 444;
          }
    ##

### Limit IP clients access

Limit specific folder to certain source IP clients only.

```
   ## the docs folder is only allowed specific IP range in 192.168.1.0/24

  location /docs/ {
  ## block one workstation
  deny    192.168.1.1;
  ## allow anyone in 192.168.1.0/24
  allow   192.168.1.0/24;
  ## drop rest of the world
  deny    all;
}
```

### SSL/TLS Configuration

Disable SSLv3(enabled by default since nginx 0.8.19)

    server {
           # SSL protocols TLS v1~TLSv1.2 are allowed. Disabed SSLv3
           ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
    }

For further details on SSL Module configuration refer to
<http://wiki.nginx.org/NginxHttpSslModule>

### SSL Module

    server {
         # enables server-side protection from BEAST attacks
         ssl_prefer_server_ciphers on;

         # Disabled insecure ciphers suite. For example, MD5, DES, RC4, PSK
          ssl_ciphers "ECDHE-RSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:DHE-RSA-AES256-GCM-SHA384:DHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256:ECDHE-RSA-AES256-SHA:ECDHE-RSA-AES128-SHA:DHE-RSA-AES256-SHA256:DHE-RSA-AES128-SHA256:DHE-RSA-AES256-SHA:DHE-RSA-AES128-SHA:ECDHE-RSA-DES-CBC3-SHA:EDH-RSA-DES-CBC3-SHA:AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA:DES-CBC3-SHA:HIGH:!aNULL:!eNULL:!EXPORT:!DES:!MD5:!PSK:!RC4:@STRENGTH";

        # -!MEDIUM：exclude encryption cipher suites using 128 bit encryption.
        # -!LOW：   exclude encryption cipher suites using 64 or 56 bit encryption algorithms
        # -!EXPORT： exclude export encryption algorithms including 40 and 56 bits algorithms.
        # -!aNULL：  exclude the cipher suites offering no authentication. This is currently the anonymous DH algorithms and anonymous ECDH algorithms.
            # These cipher suites are vulnerable to a "man in the middle" attack and so their use is normally discouraged.
        # -!eNULL：exclude the "NULL" ciphers that is those offering no encryption.
            # Because these offer no encryption at all and are a security risk they are disabled unless explicitly included.
        # @STRENGTH：sort the current cipher list in order of encryption algorithm key length.

    }

### HTTP secure Header

    # X-Frame-Options is to prevent from clickJacking attack
    add_header X-Frame-Options SAMEORIGIN;

    #  disable content-type sniffing on some browsers.
    add_header X-Content-Type-Options nosniff;

    # This header enables the Cross-site scripting (XSS) filter
    add_header X-XSS-Protection "1; mode=block";

    # This will enforce HTTP browsing into HTTPS and avoid ssl stripping attack
    add_header Strict-Transport-Security "max-age=31536000; includeSubdomains;";

refer to <https://www.owasp.org/index.php/List_of_useful_HTTP_headers>

### Limit HTTP Method

```

## Only GET, Post, PUT are allowed##
     if ($request_method !~ ^(GET
|PUT
|POST)$ ) {
         return 444;
     }
## In this case, it does not accept other HTTP method such as HEAD, DELETE, SEARCH, TRACE ##
```

In most of cases, the TRACE method is suggested to be disabled.

## References

<https://nealpoole.com/blog/2011/04/setting-up-php-fastcgi-and-nginx-dont-trust-the-tutorials-check-your-configuration/>

<http://ngx.readthedocs.org/en/latest/topics/tutorials/config_pitfalls.html>

<http://www.cyberciti.biz/tips/linux-unix-bsd-nginx-webserver-security.html>

<http://nginx.org/en/docs/http/ngx_http_core_module.html>

<http://www.tecmint.com/nginx-web-server-security-hardening-and-performance-tips/>

<http://wiki.nginx.org/NginxHttpSslModule>