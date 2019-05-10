In order to help prevent clickjacking or UI redress attacks one of the
following headers should be in all HTTP response headers.

**X-Frame-Options HTTP Response Header**

// to prevent all framing of this content **response.addHeader(
"X-FRAME-OPTIONS", "DENY" );**

// to allow framing of this content only by this site
**response.addHeader( "X-FRAME-OPTIONS", "SAMEORIGIN" );**

// to allow framing from a specific domain **response.addHeader(
"X-FRAME-OPTIONS", "ALLOW-FROM X" );**

Older browsers dont usderstand the above headers. In order to help
prevent regress attacks we may see the following code on the client side
files.

`   `**`Legacy``   ``Browser``   ``Clickjacking``   ``Defense`**
`   `

<style id="antiCJ">

body{display:none \!important;}

</style>

<script type="text/javascript">

`   if (self === top) `
`   { var antiClickjack = document.getElementByID("antiCJ"); `
`   antiClickjack.parentNode.removeChild(antiClickjack) `
`   } `
`   else { top.location = self.location; } `
`   `

</script>

To avoid click jacking or Cross Site Request Forgery of the website,
look for implementation of X-Frame-Options .Keep in mind that this code
might not work on legacy browsers. The website
<http://erlend.oftedal.no/blog/tools/xframeoptions/> does a
compatibility test on the browser’s x-frame-options support.