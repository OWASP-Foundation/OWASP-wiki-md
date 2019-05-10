# Code Snippet

**CAUTION:** This code snippet below is segmented intentionally. You are
not supposed to copy paste this code, unless you understand its risks
and how it operates. It is not verified by OWASP professional, just
composed by them. Up until now two small flaws have been reported and
fixed in this code. Also it uses regular expressions which are not even
close to a good solution for parsing HTML ([see
why](http://stackoverflow.com/questions/1732348/regex-match-open-tags-except-xhtml-self-contained-tags)),
it is just there to give you an insight on what should be done. See the
discussion page for more details.

If you need to protect against CSRF attacks in your code, this little
helper can reduce the risk:

`session_start(); //if you are copying this code, this line makes it work.`

`function store_in_session($key,$value)`
`{`
`   if (isset($_SESSION))`
`   {`
`       $_SESSION[$key]=$value;`
`   }`
`}`
`function unset_session($key)`
`{`
`   $_SESSION[$key]=' ';`
`   unset($_SESSION[$key]);`
`}`
`function get_from_session($key)`
`{`
`   if (isset($_SESSION[$key]))`
`   {`
`       return $_SESSION[$key];`
`   }`
`   else {  return false; }`
`}`

`function csrfguard_generate_token($unique_form_name)`
`{`
`   $token = random_bytes(64); // PHP 7, or via paragonie/random_compat`
`   store_in_session($unique_form_name,$token);`
`   return $token;`
`}`
`function csrfguard_validate_token($unique_form_name,$token_value)`
`{`
`   $token = get_from_session($unique_form_name);`
`   if (!is_string($token_value)) {`
`       return false;`
`   }`
`   $result = hash_equals($token, $token_value);`
`   unset_session($unique_form_name);`
`   return $result;`
`}`

`function csrfguard_replace_forms($form_data_html)`
`{`
`   $count=preg_match_all("/<form(.*?)>(.*?)<\\/form>/is",$form_data_html,$matches,PREG_SET_ORDER);`
`   if (is_array($matches))`
`   {`
`       foreach ($matches as $m)`
`       {`
`           if (strpos($m[1],"nocsrf")!==false) { continue; }`
`           $name="CSRFGuard_".mt_rand(0,mt_getrandmax());`
`           $token=csrfguard_generate_token($name);`
`           $form_data_html=str_replace($m[0],`
`               "<form{$m[1]}>`
<input type='hidden' name='CSRFName' value='{$name}' />
<input type='hidden' name='CSRFToken' value='{$token}' />`{$m[2]}`

</form>

",$form_data_html);

`       }`
`   }`
`   return $form_data_html;`
`}`

`function csrfguard_inject()`
`{`
`   $data=ob_get_clean();`
`   $data=csrfguard_replace_forms($data);`
`   echo $data;`
`}`
`function csrfguard_start()`
`{`
`   if (count($_POST))`
`   {`
`       if ( !isset($_POST['CSRFName']) or !isset($_POST['CSRFToken']) )`
`       {`
`           trigger_error("No CSRFName found, probable invalid request.",E_USER_ERROR);     `
`       } `
`       $name =$_POST['CSRFName'];`
`       $token=$_POST['CSRFToken'];`
`       if (!csrfguard_validate_token($name, $token))`
`       { `
`           throw new Exception("Invalid CSRF token.");`
`       }`
`   }`
`   ob_start();`
`   /* adding double quotes for "csrfguard_inject" to prevent: `
`          Notice: Use of undefined constant csrfguard_inject - assumed 'csrfguard_inject' */`
`   register_shutdown_function("csrfguard_inject"); `
`}`
`csrfguard_start();`

# Description and Usage

The first three functions, are an abstraction over how session variables
are stored. Replace them if you don't use native PHP sessions.

The **generate** function, creates a random secure one-time CSRF token.
If SHA512 is available, it is used, otherwise a 512 bit random string in
the same format is generated. This function also stores the generated
token under a unique name in session variable.

The **validate** function, checks under the unique name for the token.
There are three states:

  - Sessions not active: validate succeeds (no CSRF risk)
  - Token found but not the same, or token not found: validation fails
  - Token found and the same: validation succeeds

Either case, this function removes the token from sessions, ensuring
one-timeness.

The **replace** function, receives a portion of html data, finds all

<form>

occurrences and adds two hidden fields to them: CSRFName and CSRFToken.
If any of these forms has an attribute or value ***nocsrf***', the
addition won't be performed (note that using default inject and detect
breaks with this).

The other two functions, **inject** and **start** are a demonstration of
how to use the other functions. Using output buffering on your entire
output is not recommended (some libraries might dump output buffering).
This default behavior, enforces CSRF tokens on all forms using POST
method. It is assumed that no sensitive operations with GET method are
performed in the application, as required by
[RFC 2616](http://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html#sec9.1.1).

To test this code, append the following HTML to it:

<form method='post'>

<input type='text' name='test' value='<?php echo "testing"?>`' />`
<input type='submit' />

</form>

<form class='nocsrf'>

</form>

# Author and License

This piece of code is by [Abbas Naderi
Afooshteh](mailto:abbas.naderi@owasp.org) from OWASP under Creative
Commons 3.0 License.

Contributions from Krzysztof Kotowicz \<krzysztof.kotowicz at
securing.pl\>, Jakub Kałużny \<jakub.artur.kaluzny at g\>, Nick Le
Mouton \<nick at noodles.net dot nz\>