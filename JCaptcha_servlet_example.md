In this example, a simple Java servlet is used to generate a captcha
image that is displayed alongside input boxes for username and password
on a simulated login page (see Figure 1 below). The user must enter his
credentials and the letters appearing in the captcha image. Once the
user submits the form, the same servlet validates the input and sets a
flag in the user's session. An appropriate response is shown on the
results page indicating whether or not they passed the captcha
challenge. Note: the browser must support session cookies. Also, the
username and password inputs are ignored in this example (something you
might not want to do in a real-life scenario\!).

![Simple-captcha-servlet-loginpage.png](Simple-captcha-servlet-loginpage.png
"Simple-captcha-servlet-loginpage.png")

The source for the login jsp page is presented below. Note that the src
attribute of the captcha image is "/captcha-demos/simple". In web.xml,
we have set "simple" to map to `SimpleCaptchaServlet`. The image tag
results in a GET call to our servlet, which does the work necessary to
generate the captcha image. The login form submits via POST method to
the same servlet.

<tt>

`<%@ page language="java" %>`
`<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"`
`"`<http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd>`">`

<html ns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">

<head>

<title>

Using JCaptcha - A Simple Captcha Servlet

</title>

<style type="text/css">

`td`
`{ font-family: Verdana, Tahoma, Arial, Helvetica; font-size: 10pt;`
`  background-color: #FFFFFF; margin-left: 0pt`
`}`

</style>

</head>

<body>

<h2>

Using JCaptcha: A Simple Captcha Servlet

</h2>

`<form name="SimpleServletForm" `**`action="/captcha-demos/simple"``
 ``method="post"`**`>`
<input type="hidden" name="hidCaptchaID" value="<%= session.getId() %>`"/>`

<table border="0" cellspacing="0" cellpadding="3">

<tr>

<td>

Username:

</td>

<td align="center">

<input type="text" name="inUsername" value="joeuser"/>

</td>

</tr>

<tr>

<td>

Password:

</td>

<td align="center">

<input type="password" name="inPassword"
     value="somepassword"/>

</td>

</tr>

<tr>

<td valign="middle">

Enter these letters:
\<img **src="/captcha-demos/simple"** align="middle" alt="Enter the

`    characters appearing in this image" border="1"/>`

</td>

<td>

<input type="text" name="inCaptchaChars"/>

</td>

</tr>

<tr>

<td colspan="2" align="right">

<input type="submit"
     value="Submit"/>

</td>

</tr>

<tr>

<td colspan="2" align="center">



(refresh

`    page to generate a new image)`

</td>

</tr>

</table>

</form>

</body>

</html>

</tt>

Source code for `SimpleCaptchaServlet` is shown below. The `doGet()`
method handles the captcha image generation. Each captcha image must
have an associated ID that is used as the key. The session ID is a
convenient captcha ID in this case. The `MyCaptchaService` class (shown
later) is a singleton that utilizes a JCaptcha built-in class called
`DefaultManageableImageCaptchaService`. This class provides a default
Gimpy-based captcha image, management of associated ID's, and validation
of user input. This servlet supports a captcha image that is either PNG
or JPG format. A servlet initialization parameter controls which type is
used.

<tt>

`package org.owasp.captcha;`
`import com.octo.captcha.service.CaptchaServiceException;`
`import javax.servlet.*;`
`import javax.servlet.http.*;`
`import java.awt.image.BufferedImage;`
`import java.io.ByteArrayOutputStream;`
`import java.io.IOException;`
`import java.util.Map;`
`import javax.imageio.ImageIO;`
`public class `**`SimpleCaptchaServlet`**` extends HttpServlet`
`{`
`  String sImgType = null;`
`  public void init( ServletConfig servletConfig ) throws ServletException`
`  {`
`    super.init( servletConfig );`

`    // For this servlet, supported image types are PNG and JPG.`
`    sImgType = servletConfig.getInitParameter( "ImageType" );`
`    sImgType = sImgType==null ? "png" : sImgType.trim().toLowerCase();`
`    if ( !sImgType.equalsIgnoreCase("png") && !sImgType.equalsIgnoreCase("jpg") &&`
`    !sImgType.equalsIgnoreCase("jpeg") )`
`    {`
`      sImgType = "png";`
`    }`
`  }`

`  protected void doGet( HttpServletRequest request, HttpServletResponse response ) `
`  throws ServletException, IOException`
`  {`
`    ByteArrayOutputStream imgOutputStream = new ByteArrayOutputStream();`
`    byte[] captchaBytes;`

`    if ( request.getQueryString()!=null )`
`    {`
`      response.sendError( HttpServletResponse.SC_INTERNAL_SERVER_ERROR, "GET request should have no query string." );`
`      return;`
`    }`
`    try`
`    {`
`      // Session ID is used to identify the particular captcha.`
`      String captchaId = request.getSession().getId();`

`      // Generate the captcha image.`
`      BufferedImage challengeImage = `**`MyCaptchaService.getInstance().getImageChallengeForID`**`(`
`      captchaId, request.getLocale() );`
`      ImageIO.write( challengeImage, sImgType, imgOutputStream );`
`      captchaBytes = imgOutputStream.toByteArray();`

`      // Clear any existing flag.`
`      request.getSession().removeAttribute( "PassedCaptcha" );`
`    }`
`    catch( CaptchaServiceException cse )`
`    {`
`       System.out.println( "CaptchaServiceException - " + cse.getMessage() );`
`       response.sendError( HttpServletResponse.SC_INTERNAL_SERVER_ERROR, "Problem generating captcha image." );`
`       return;`
`    }`
`    catch( IOException ioe )`
`    {`
`       System.out.println( "IOException - " + ioe.getMessage() );`
`       response.sendError( HttpServletResponse.SC_INTERNAL_SERVER_ERROR, "Problem generating captcha image." );`
`       return;`
`    }`

`    // Set appropriate http headers.`
`    response.setHeader( "Cache-Control", "no-store" );`
`    response.setHeader( "Pragma", "no-cache" );`
`    response.setDateHeader( "Expires", 0 );`
`    response.setContentType( "image/" + (sImgType.equalsIgnoreCase("png") ? "png" : "jpeg") );`

`    // Write the image to the client.`
`    ServletOutputStream outStream = response.getOutputStream();`
`    outStream.write( captchaBytes );`
`    outStream.flush();`
`    outStream.close();`
`  }`

`  protected void doPost( HttpServletRequest request, HttpServletResponse response ) `
`  throws ServletException, IOException`
`  {`
`    // Get the request params.`
`    Map paramMap = request.getParameterMap();`
`    if ( paramMap.isEmpty() )`
`    {`
`      response.sendError( HttpServletResponse.SC_METHOD_NOT_ALLOWED, "Post method not allowed without parameters." );`
`      return;`
`    }`
`    String[] arr1 = (String[])paramMap.get( "hidCaptchaID" );`
`    String[] arr2 = (String[])paramMap.get( "inCaptchaChars" );`
`    if ( arr1==null `

| | arr2==null )

`    {`
`      response.sendError( HttpServletResponse.SC_INTERNAL_SERVER_ERROR, "Expected parameters were not found." );`
`      return;`
`    }`

`    String sessId = request.getSession().getId();`
`    String incomingCaptchaId = arr1.length>0 ? arr1[0] : "";`
`    String inputChars = arr2.length>0 ? arr2[0] : "";`

`    // Check validity and consistency of the data.`
`    if ( sessId==null `

| | incomingCaptchaId==null | | \!sessId.equals(incomingCaptchaId) )

`    {`
`      response.sendError( HttpServletResponse.SC_INTERNAL_SERVER_ERROR, "Browser must support session cookies." );`
`      return;`
`    }`

`    // Validate whether input from user is correct.`
`    System.out.println( "Validating - inputChars are: " + inputChars );`
`    boolean passedCaptchaTest = `**`validateCaptcha`**`( incomingCaptchaId, inputChars );`

`    // Set flag into session.`
`    request.getSession().setAttribute( "PassedCaptcha", new Boolean(passedCaptchaTest) );`

`    // Forward request to results page.`
`    RequestDispatcher rd = getServletContext().getRequestDispatcher( "/results.jsp" );`
`    rd.forward( request, response );`
`  }`

`  private boolean validateCaptcha( String captchaId, String inputChars )`
`  {`
`    boolean bValidated = false;`
`    try`
`    {`
`      bValidated = `**`MyCaptchaService.getInstance().validateResponseForID`**`( captchaId, inputChars );`
`    }`
`    catch( CaptchaServiceException cse )`
`    {}`
`    return bValidated;`
`  }`
`}`

</tt>

Below is the source code for `MyCaptchaService`.

<tt>

`package org.owasp.captcha;`
`import com.octo.captcha.service.image.ImageCaptchaService;`
`import com.octo.captcha.service.image.DefaultManageableImageCaptchaService;`
`public class `**`MyCaptchaService`**
`{`
`  // a singleton class`
`  private static ImageCaptchaService instance = new `**`DefaultManageableImageCaptchaService()`**`;`
`  public static ImageCaptchaService getInstance()`
`  {`
`    return instance;`
`  }`
`}`

</tt>

Depending on the outcome of the captcha validation, either a Boolean
"true" or Boolean "false" object is set into the user's session in the
form of an attribute. The request is then forwarded on to the
results.jsp page. Assuming the user entered the correct letters, the
page below is displayed.

![Simple-captcha-servlet-resultspage.png](Simple-captcha-servlet-resultspage.png
"Simple-captcha-servlet-resultspage.png")

Here is the source for results.jsp:

<tt>

`<%@ page language="java" %>`
`<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"`
`"`<http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd>`">`

<html ns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">

<head>

<title>

Captcha Demo - Servlet

</title>

</head>

<body>

`<% Boolean B = (Boolean)session.getAttribute( "PassedCaptcha" );`
`   if ( B!=null && B.booleanValue() )`
`   {`
`%>`
`  Congrats!  You passed the Captcha test!`
`<% } else { %>`
`  Sorry, you failed the Captcha test.`
`<% } %>`
`  `

Please <a href="login.jsp">Try Again</a>

</body>

</html>

</tt>