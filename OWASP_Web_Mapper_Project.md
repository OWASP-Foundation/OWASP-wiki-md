# Main

<div style="width:100%;height:160px;border:0,margin:0;overflow: hidden;">

![OWASP_Project_Header.jpg](OWASP_Project_Header.jpg
"OWASP_Project_Header.jpg")

</div>

<table>
<tbody>
<tr class="odd">
<td><h2 id="owasp_web_mapper_project">OWASP Web Mapper Project</h2>
<p>What if there are quite a few web applications under your organization, but nobody seems to know all of them (before the talk of application risk assessment)? Then this project may be a right fit for you.</p>
<p>This project is designed to perform the web application asset discovery and auto tracking with scale.</p>
<h2 id="description">Description</h2>
<p>A pure Ruby library for the web application asset discovery and tracking. The tool is useful when you're handling a larger size organization with multiple Internet domains and networks registered under the name. Where both legacy and new web applications are omni-present but nobody seems to be able to provide a complete list of application URLs to you. Yes you can always do it the old way by using tool sets such as NMAP, OWASP Zap web crawler, along with others. But such tool sets could quickly become too much manual-driven and inaccurate, if not impossible. In the contrary, once setup, this project will help you quickly identify all the 'unknown' web application asset, and keep track of them automatically. If you are serious about your organization's Internet web application exposure, this might be the perfect all-in-one footprinting tool you're looking for.</p>
<p>Built as an open source project, the source code is both free and scalable. You're welcome to keep building on top of the current code base, or include it as part of your larger project distribution.</p>
<h2 id="licensing">Licensing</h2>
<p>'''The OWASP Web Mapper Project is free to use. In fact it is encouraged!</p>
<p>The OWASP Security Principles are licensed under the <a href="https://github.com/yangsec888/wmap/blob/master/LICENSE.txt">Apache 2.0 license</a>, so you can copy, distribute and transmit the work, and you can adapt it, and use it commercially, but all provided that you attribute the work and if you alter, transform, or build upon this work, you may distribute the resulting work only under the same or similar license to this one.</p></td>
<td><h2 id="what_is_owasp_web_mapper_project">What is OWASP Web Mapper Project?</h2>
<p>The goal is to help you better identify, and keep track of the web application asset under your watch. Ideally we could document various reverse-engineering techniques using by this project and publish it through the OWASP Press. Of course, it will always remain freely available, and any money collected will go directly into the project and to the OWASP Foundation.</p>
<h2 id="demo">Demo</h2>
<ul>
<li><a href="http://wmap.io/">Demo</a> A demo web app exploring WMAP library power.</li>
</ul>
<h2 id="project_code_and_documents">Project Code and Documents</h2>
<ul>
<li><a href="https://github.com/yangsec888/wmap">Latest WMAP source tree.</a></li>
<li><a href="https://github.com/yangsec888/www_wmap">WMAP web app demo built in Ruby on Rails 5+</a></li>
</ul></td>
<td><h2 id="related_projects">Related Projects</h2>
<ul>
<li><a href="OWASP_Zed_Attack_Proxy_Project" title="wikilink">OWASP_Zed_Attack_Proxy_Project</a></li>
</ul>
<h2 id="news_and_events">News and Events</h2>
<ul>
<li>[January 1 2018] OWASP Web Mapper demo web application released.</li>
<li>[August 1 2015] OWASP Web Mapper Project created.</li>
</ul>
<h2 id="project_leader">Project Leader</h2>
<ul>
<li><a href="https://www.owasp.org/index.php/User:Yang_Li">Sam (Yang) Li</a></li>
</ul>
<h2 id="in_print">In Print</h2>
<p>I'm working on project document. But it's far from become a book at this moment. Instead, please refer to the project hosting site for more project document.</p></td>
</tr>
</tbody>
</table>

# FAQs

## Installation

1.  The easiest way to install WebMapper is by using Ruby Gems. Download
    the latest gem 'wmap-x.x.x.gem' into the local file system. Then
    install it from your shell environment:

`$ gem install wmap-x.x.x.gem --no-rdoc`

## Dependency

You need the Ruby 1.9.2 or above in order to use this program. In
addition, I developed and tested the code in a Ubantu Linux VM with Ruby
1.9.3.

  - You need to setup Ruby 1.9.x environment. In my test environment, I
    was able to set it up with RVM. Please refer to this page for more
    installation information: <http://www.ruby-lang.org/en/downloads/>

<!-- end list -->

  - In addition, the following Ruby GEM dependency are needed by
    different components of this software:

:\# require "uri"

:\# require "open-uri"

:\# require "open_uri_redirections"

:\#require "nokogiri"

:\#require "net/http"

:\#require "httpclient"

:\#require "net/ping"

:\#require "netaddr"

:\#require "socket"

:\#require "openssl"

:\#require "whois"

:\#require "resolv"

:\#require "geoip"

:\#require "parallel"

:\#require "dnsruby"

  - Install dependency gem "uri" example

` $ gem install uri`

  - Ruby-whois gem patches

This software also depends on a patched version of Ruby gem
ruby-whois-2.7.0 (http://www.ruby-whois.org/) for the domain whois
lookup feature. For better result, you could manually add the patches
into your local whois gem installation directory as shown below:

` $ cp whois_patches/* [Your_ruby_whois_gem_path]/whois/lib/whois/record/parser/`

Or you can directly download the branched whois gem from this repository
- <https://github.com/yangsec888/whois>

## Before Using This Program

You need to define a scope for the program to run successful. The scope
includes both your legitimate Internet domain, and your public network
block in the CIDR format.

To add your Internet domain into the scope, use the build-in shell
command below:

` $ trust XYZ.COM`

To add your public network block into the scope:

` $ trust x.x.x.x/x`

## Automatic Discovery and Tracking

` $ wmap <seed file | target host | target url | target IP or network cidr>`

The above utility is intelligent enough to take argument as either a
seed file, or a string such as a host, an IP, a network block, or a URL.
The new discoveries will be automatically tracked in the data file
'lib/wmap/data/target_sites'.

` Note: seed file - mix of url, cidr and domain seed, one entry per line.`
`               url seed - known URL(s) for further discovery via the web crawler.`
`               cidr seed - list of known network blocks, for discovering web service via port scanning; it is also used to validate if the web service has a known IP (internal hosted).`
`               domain seed - validated internet domain to be used for DNS record brute-forcing; it is also used to validate the ownership of found web service.`

## Dump Out Discovery Database

You can dump out the program output by using the build-in utility
'wdump' as shown below:

` $ wdump [output file name from you]`

The above utility will dump out the discovery database into a single
file as program output. Currently, the supported file format is
Comma-separated Value (.csv) and Extensible Markup Language (.xml)

## Other Build-in Utilities

You may need to update your sset repository from time to time. For this
purpose, ‘wmap’ provide three utilities ‘wcheck’, ‘wadd’ and ‘wdel’ to
perform the tasks for you. For example, you can check out the status of
a site, as shown below:

` $ wcheck `<https://www.owasp.org/>
` {"ip"=>"104.130.192.89", "port"=>443, "url"=>"https://www.owasp.org/", "code"=>301, "redirection"=>"https://www.owasp.org/index.php/Main_Page", "md5"=>"d41d8cd98f00b204e9800998ecf8427e", "server"=>"Apache", "timestamp"=>2015-09-02 13:32:31 -0400, "status"=>"ext_hosted"}`

You may want to use 'wadd' utility to add it, as shown below:

` $ wadd `<https://www.owasp.org/>

You may want to use 'wdel' utility to delete it, as shown below:

` $ wdel `<https://www.owasp.org/>

## More Usage Examples

There are also some code examples under the 'demos' folder of this
package. The examples show how to use the 'wmap' API to get your job
done easily. Please check out the code - they should be easy and
straightforward to be understood.

## More document(s)

The software comes with the Ruby doc during your installation as shown
above. For your convenience, the Ruby doc is also distributed with the
software. You can navigate to the 'doc' folder of your local
installation, and click the 'index.html' to open the start page in your
favorite browser. You can also download the wmap-x.x.x.rdoc.zip
documentation package alone from the hosting site, unzip and open the
doc/index.html in your browser.

If you need additional documentation / information other than this
README file and the Ruby document package, please be patient - as I'm
still working on it.

## How do I report the bugs, or maybe require some new features?

Contact the developer Yang Li directly at his email 'yang.li@owasp.org'.

## How can I participate in your project?

All you have to do is make the Project Leader's aware of your available
time to contribute to the project. It is also important to let the
Leader's know how you would like to contribute and pitch in to help the
project meet it's goals and milestones. There are many different ways
you can contribute to an OWASP Project, but communication with the leads
is key.

## If I am not a programmer can I participate in your project?

Yes, you can certainly participate in the project if you are not a
programmer or technical. The project needs different skills and
expertise and different times during its development. Currently, we are
looking for QA tester, front-end builder, document writers, graphic
designers, and a project administrator.

# Acknowledgements

## Contributors

The OWASP Web Mapper Project is originally developed by Yang Li. A live
update of project [contributors can be found
here](https://github.com/yangsec888/wmap/blob/master/CREDIT.txt).

The first contributors to the project are:

  - [Yang Li](https://www.owasp.org/index.php/User:Yang_Li)
  - \[Your name here\]

# Road Map

<span> Please refer to TODO file at code repository for additional
information:

  - <https://github.com/yangsec888/wmap/blob/master/TODO>

</span> 

# Getting Involved

Involvement in the development and promotion of the OWASP Web Mapper
Project is encouraged\! You do not have to be a developer in order to
contribute. Some of the ways you can get involved and contribute:

  - Join the project [Mailing
    List](https://lists.owasp.org/mailman/listinfo/owasp-web-mapper-project).
  - Help QA test the project.
  - Help build a user-friendly front-end.
  - Project administration support.
  - Wiki editing support.
  - Writing support for the book.

If you can help, please sign up a [GITHUB](https://github.com/) account,
then [notify me](mailto:yang.li@owasp.org).

__NOTOC__ <headertabs />

[Category:OWASP Project](Category:OWASP_Project "wikilink")
[Category:OWASP_Builders](Category:OWASP_Builders "wikilink")
[Category:OWASP_Defenders](Category:OWASP_Defenders "wikilink")
[Category:OWASP_Document](Category:OWASP_Document "wikilink")