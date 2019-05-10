## **Where can XSS occur??**

### HTML Body Context

\<span\>UNTRUSTED DATA\</span\>

### **HTML Attribute Context**


\<input type="text" name="fname" value="UNTRUSTED DATA"\>
attack: "\>

<script>

/\* bad stuff \*/

</script>



### **HTTP GET Parameter Context**


\<a href="/site/search?value=UNTRUSTED DATA"\>clickme\</a\>
attack: " onclick="/\* bad stuff \*/"

### **URL Context**


\<a href="UNTRUSTED URL"\>clickme\</a\> \<iframe src="UNTRUSTED URL"
/\>
attack: <javascript:/>\* BAD STUFF \*/

### **CSS Value Context**



<div style="width: UNTRUSTED DATA;">

Selection

</div>

attack: expression(/\* BAD STUFF \*/)

### **JavaScript Variable Context**



<script>

var currentValue='UNTRUSTED DATA';

</script>



<script>

someFunction('UNTRUSTED DATA');

</script>

attack: ');/\* BAD STUFF \*/

### **JSON Parsing Context**


JSON.parse(UNTRUSTED JSON DATA)