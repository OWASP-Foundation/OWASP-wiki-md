<noinclude></noinclude> __NOTOC__

## The Presentation

CAPTCHAs are a potent mechanism to prevent web applications against
automated form submissions. To analyze the strength of CAPTHA
deployments on the internet, a research spanning hundreds of high
traffic websites and several CAPTCHA service providers was conducted.
The research looked at CAPTCHA schemes, CAPTCHA implementation and
Verification mechanisms. During the research, several interesting
implementation flaws and attacks were identified that will be discussed
during the presentation. Some of these flaws/attacks include CAPTCHA
fixation, CAPTCHA Rainbow Tables, In-Session CAPTCHA Bruteforcing, OCR
Assisted CAPTCHA Bruteforcing, Chosen CAPTCHA Text Attack, CAPTCHA
Accumulation etc'
It was observed that an alarming number of visual CAPTCHAs schemes could
be broken by combination of good image preprocessing and Optical
Character Recognition (OCR) engines. TesserCap was thus written to test
CAPTHA designs based upon these observations.
TesserCap is a GUI based, highly flexible and first of its kind CAPTCHA
analysis tool. TesserCap retrieves CAPTCHAs from the target website and
solves those locally. Each CAPTCHA is subjected to TesserCap's 8 stage
image preprocessing module and the OCR engine. The image preprocessing
algorithms work around color complexities, spatial irregularities, and
other types of random noise that developers introduce into the CAPTCHAs
to achieve higher detection rates.

## The Speakers

<table>

<tr>

<td>

### Gursev Singh Kalra

![AppSecDC12-gursev.jpg](AppSecDC12-gursev.jpg
"AppSecDC12-gursev.jpg")Gursev Singh Kalra serves as a Managing
Consultant at Foundstone, McAfee. Gursev was a speaker at security
conferences like ToorCon, NullCon and ClubHack. Gursev has authored an
open source SSL cipher enumeration tool SSLSmart, CAPTCHA Solving tool
TesserCap and a whitepaper on Mobile Application Security Testing.
Gursev has also developed several internal tools, web applications and
loves to code in Ruby, Ruby on Rails and C\#.

</td>

</tr>

</table>

<noinclude></noinclude>