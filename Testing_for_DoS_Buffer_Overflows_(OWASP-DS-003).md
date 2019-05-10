## Brief Summary

In this test we check whether it is possible to cause a denial of
service condition by overflowing one or more data structures of the
target application.

## Description of the Issue

Any language where the developer has direct responsibility for managing
memory allocation, most notably C & C++, has the potential for a buffer
overflow. While the most serious risk related to a buffer overflow is
the ability to execute arbitrary code on the server, the first risk
comes from the denial of service that can happen if the application
crashes. Buffer overflows are discussed in more detail elsewhere in this
testing document, but we will briefly give an example as it relates to
an application denial of service.

The following is a simplified example of vulnerable code in C:

    void overflow (char *str) {
       char buffer[10];
       strcpy(buffer, str); // Dangerous!
    }

    int main () {
      char *str = "This is a string that is larger than the buffer of 10";
      overflow(str);
    }

If this code example were executed, it would cause a segmentation fault
and dump core. The reason is that strcpy would try to copy 53 characters
into an array of 10 elements only, overwriting adjacent memory
locations. While this example above is an extremely simple case, the
reality is that in a web based application there may be places where the
user input is not adequately checked for its length, making this kind of
attack possible.

## Black Box Testing

Refer to the [Testing for Buffer
Overflow](Testing_for_Buffer_Overflow_\(OWASP-DV-014\) "wikilink")
section for how to submit a range of lengths to the application looking
for possible locations that may be vulnerable. As it relates to a DoS,
if you have received a response (or a lack of) that makes you believe
that the overflow has occurred, attempt to make another request to the
server and see if it still responds.

## Gray Box Testing

Please refer to the [Testing for Buffer
Overflow](Testing_for_Buffer_Overflow_\(OWASP-DV-014\) "wikilink")
section of the Guide for detailed information on this testing.

[category:Denial of Service
Attack](category:Denial_of_Service_Attack "wikilink") [category:Buffer
Overflow Attack](category:Buffer_Overflow_Attack "wikilink")