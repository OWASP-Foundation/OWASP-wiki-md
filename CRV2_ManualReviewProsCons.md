# Manual Review - Pros and Cons

Manual review is sited when a risk based approach to the code review is
required. Risk based code review works by.

1\. Identification of the trust boundaries in the code. 2.
Identification of data paths and storage classes. 3. Identification of
authorisation components. 4. Identification of authentication
components. 5. Review of input validation and encoding methods. 6.
Review of logging components.

Manual review is good for :

Data leakage detection Resource usage/exhaustion detection Business
Logic review\* Denial of service Deep Dive review

**Not so good for:** Business Logic review\* Level of coverage

## Choosing a static analysis tool

Choosing a static analysis tool is a difficult task since there are a
lot of choices. The comparison charts below should help you decide which
tool is right for you. This list is not exhaustive. The first thing to
do is to look to for a tool that supports the programming language of
your choice. You also have to decide whether you want a commercial tool
or a free one. Usually the commercial tools have more features and are
more reliable than the free ones. The major commercial tools are equally
effective but their usability might differ. Next, there is the type of
analysis you are looking for: Security or Quality, Static or Dynamic
analysis. You should also check the compatibility of the tool with your
programming environment. This was the easy part to narrow the choice
down to a few tools. The next step requires you to do some work since it
is quite subjective. The best thing to do is to test a few tools to see
if you are satisfied with different aspects such as the user experience,
the reporting of vulnerabilities, the level of false positives, the
customization, the customer support… The choice should not be based on
the number of features, but on the features that you need and how they
could be integrated in your SDLC. Also, before choosing the tool, the
security expertise of the targeted users should be clearly evaluated in
order to choose an appropriate tool.

### **Free static analysis tools**

![<File:Free_static_analysis_tools.png>](Free_static_analysis_tools.png
"File:Free_static_analysis_tools.png")
![<File:legendfree.png>](legendfree.png "File:legendfree.png")

### **Commerical static analysis tools**

![<File:Commercial_static_analysis_tools.png>](Commercial_static_analysis_tools.png
"File:Commercial_static_analysis_tools.png")
![<File:legendstatic.png>](legendstatic.png "File:legendstatic.png")

![<File:Owasp_Benchmark_Static_analysis_tools_1.1.pptx>](Owasp_Benchmark_Static_analysis_tools_1.1.pptx
"File:Owasp_Benchmark_Static_analysis_tools_1.1.pptx")