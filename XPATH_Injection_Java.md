Last revision (mm/dd/yy): **08/14/2016**

## Injection context

Some applications use XML based datastore and sometimes XPATH query
language to retrieve data from theses stores. The application can
construct XPATH query expression from user input in order to select user
dedicated data.

## Injection objective

The objective of the injection is to submit a piece of XPATH language
that will change the normal behavior of the target expression in order
to retrieve more or differents data than expected.

## Injection examples

For the examples we will take a case of an application that store
employees informations using XML store with this structure:

    <?xml version="1.0" encoding="utf-8"?>
    <employees>
      <employee id="AS789" firstname="John" lastname="Doo" annualsalary="70000"/>
      <employee id="AS719" firstname="Isabela" lastname="Dobora" annualsalary="90000"/>
      <employee id="AS219" firstname="Eric" lastname="Lambert" annualsalary="65000"/>
    </employees>

The XPATH expression to select an employee node used by application is:

    /employees/employee[@id='EMPLOYEE_ID']

The code (JavaEE6 Servlet for example) used to perform selection is:

    package org.owasp.javaproject.xpathinjection;

    import java.io.IOException;
    import java.io.StringReader;
    import java.util.List;

    import javax.servlet.ServletException;
    import javax.servlet.annotation.WebServlet;
    import javax.servlet.http.HttpServlet;
    import javax.servlet.http.HttpServletRequest;
    import javax.servlet.http.HttpServletResponse;
    import javax.xml.parsers.DocumentBuilder;
    import javax.xml.parsers.DocumentBuilderFactory;

    import org.jaxen.XPath;
    import org.jaxen.dom.DOMXPath;
    import org.w3c.dom.Document;
    import org.w3c.dom.Element;
    import org.xml.sax.InputSource;

    /**
     * Sample service to retrieve employees salary
     */
    @SuppressWarnings("serial")
    @WebServlet("/EmployeesSalaryService")
    public class EmployeesSalaryService extends HttpServlet {

        private static final String DATASOURCE_XML = "Put XML Structure above here";

        /**
         * {@inheritDoc}
         *
         * @see javax.servlet.http.HttpServlet#doGet(javax.servlet.http.HttpServletRequest, javax.servlet.http.HttpServletResponse)
         */
        @SuppressWarnings("rawtypes")
        @Override
        protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
            try {
                // For the sample we load the XML Document at each request but this not a good way for real application.....
                DocumentBuilderFactory factory = DocumentBuilderFactory.newInstance();
                DocumentBuilder builder = factory.newDocumentBuilder();
                Document doc = builder.parse(new InputSource(new StringReader(DATASOURCE_XML)));

                // Retrieve employee ID from the input HTTP request
                String eID = request.getParameter("employeeID");
                if (eID == null) {
                    eID = "";
                }

                // Create XPATH expression
                String xpathExpr = "/employees/employee[@id='" + eID + "']";
                XPath expression = new DOMXPath(xpathExpr);

                // Apply expression on XML document
                List nodes = expression.selectNodes(doc);
                for (int i = 0; i < nodes.size(); i++) {
                    Element employee = (Element) nodes.get(i);
                    response.getWriter().print(employee.getAttribute("lastname")
                    + " "
                    + employee.getAttribute("firstname")
                    + " : "
                    + employee.getAttribute("annualsalary")
                    + "<br>");
                }
            } catch (Exception e) {
                response.sendError(HttpServletResponse.SC_BAD_REQUEST);
                e.printStackTrace();
            }
        }

    }

Here the sensitive information is the annual salary then it's will be
the target of the injection.

The application expect to receive, for the employee ID, an value like
"AS789" but what is the application behavior if a user submit another
value pattern ?

Sample value n°1:

    '%20or%20'1'='1

**Result**: All employees nodes are selected (in this case the user do
not known the XML structure).

![<File:XPATHInjection01.png>](XPATHInjection01.png
"File:XPATHInjection01.png")

Sample value n°2:

    '%20or%20fn:contains(fn:lower-case(@lastname),'dobora')%20or%20'

**Result**: Employee where the last name contains "dobora" is selected
(in this case the user has guessed the XML structure).

![<File:XPATHInjection02.png>](XPATHInjection02.png
"File:XPATHInjection02.png")

## Injection countermeasure n°1

Input used into an XPATH expression must not contains any of the
characters below:

    ( ) = ' [ ] : , * / WHITESPACE

According to our example context, the modification to apply could be to
create an application transversal utility method checking the presence
of characters above and rejecting the value submitted if it's contains
any one.

Checking utility method example:

    public boolean checkValueForXpathInjection(String value) throws Exception {
        boolean isValid = true;
        if ((value != null) && !"".equals(value)) {
            String xpathCharList = "()='[]:,*/ ";
            // Always to avoid encoding evading....
            String decodedValue = URLDecoder.decode(value, Charset.defaultCharset().name());
            for (char c : decodedValue.toCharArray()) {
                if (xpathCharList.indexOf(c) != -1) {
                    isValid = false;
                    break;
                }
            }
        }
        return isValid;
    }

Checking utility use example:

    /**
     * {@inheritDoc}
     *
     * @see javax.servlet.http.HttpServlet#doGet(javax.servlet.http.HttpServletRequest, javax.servlet.http.HttpServletResponse)
     */
    @SuppressWarnings("rawtypes")
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        try {

            // Check input
            if (!checkValueForXpathInjection(request.getParameter("employeeID"))) {
                response.sendError(HttpServletResponse.SC_BAD_REQUEST);
                // Trace injection
                // Exit
                return;
            }

            .....

            }
        } catch (Exception e) {
            response.sendError(HttpServletResponse.SC_BAD_REQUEST);
            e.printStackTrace();
        }
    }

## Injection countermeasure n°2

Using variable into XPATH expression with a variable resolver enabled
evaluator can help to prevent injections (like prepared statement for
SQL injection).

Example of variable resolver:

    package org.owasp.javaproject.xpathinjection;

    import java.util.HashMap;
    import java.util.Map;

    import javax.xml.namespace.QName;
    import javax.xml.xpath.XPathVariableResolver;

    /**
     * Resolver in order to define parameter for XPATH expression.
     *
     */
    @SuppressWarnings("static-method")
    public class SimpleVariableResolver implements XPathVariableResolver {

        private final Map<QName, Object> vars = new HashMap<QName, Object>();

        /**
         * External methods to add parameter
         *
         * @param name Parameter name
         * @param value Parameter value
         */
        public void addVariable(QName name, Object value) {
            vars.put(name, value);
        }

        /**
         * {@inheritDoc}
         *
         * @see javax.xml.xpath.XPathVariableResolver#resolveVariable(javax.xml.namespace.QName)
         */
        @Override
        public Object resolveVariable(QName variableName) {
            return vars.get(variableName);
        }

    }

Example of use of the variable resolver:

    /**
     * {@inheritDoc}
     *
     * @see javax.servlet.http.HttpServlet#doGet(javax.servlet.http.HttpServletRequest, javax.servlet.http.HttpServletResponse)
     */
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        try {

            // For the sample we load the XML Document at each request but
                    //this not a good way for real application.....
            DocumentBuilderFactory factory = DocumentBuilderFactory.newInstance();
            DocumentBuilder builder = factory.newDocumentBuilder();
            Document doc = builder.parse(new InputSource(new StringReader(DATASOURCE_XML)));

            // Retrieve employee ID from the input HTTP request
            String eID = request.getParameter("employeeID");
            if (eID == null) {
                eID = "";
            }

            // Create and configure parameter resolver
            SimpleVariableResolver variableResolver = new SimpleVariableResolver();
            variableResolver.addVariable(new QName("eID"), eID);

            // Create and configure XPATH expression
            XPath xpath = XPathFactory.newInstance().newXPath();
            xpath.setXPathVariableResolver(variableResolver);
            XPathExpression xPathExpression = xpath.compile("/employees/employee[@id=$eID]");

            // Apply expression on XML document
            Object nodes = xPathExpression.evaluate(doc, XPathConstants.NODESET);
            NodeList nodesList = (NodeList) nodes;
            for (int i = 0; i < nodesList.getLength(); i++) {
                Element employee = (Element) nodesList.item(i);
                response.getWriter().print(employee.getAttribute("lastname")
                            + " " + employee.getAttribute("firstname") + " : "
                            + employee.getAttribute("annualsalary") + "<br>");
            }
        }
        catch (Exception e) {
            response.sendError(HttpServletResponse.SC_BAD_REQUEST);
            e.printStackTrace();
        }
    }

[Category:Java](Category:Java "wikilink") [Category:Injection
Attack](Category:Injection_Attack "wikilink")