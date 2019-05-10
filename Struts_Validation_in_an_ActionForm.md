  - struts-config.xml

<!-- end list -->

```
    <struts-config>
        <form-beans>
            <form-bean name="logonForm" type="net.jcj.LogonForm"/>
        </form-beans>
        <action-mappings>
            <action path="/Logon" forward="/pages/Logon.jsp"/>
            <action path="/LogonSubmit" type="app.jcj.LogonAction" name="logonForm"
               scope="request" validate="true" input="/pages/Logon.jsp">
                <forward name="success" path="/pages/Welcome.jsp"/>
                <forward name="failure" path="/pages/Logon.jsp"/>
            </action>
        </action-mappings>
        <message-resources parameter="resources.application"/>
    </struts-config>
```

  - net.jcj.LogonForm

<!-- end list -->

    package net.jcj;

    import javax.servlet.http.HttpServletRequest;
    import org.apache.struts.action.*;

    public class LogonForm extends ActionForm
    {
      private String userId = null;
      private String password = null;

      public void setUserId (String userId){
        this.userId = userId ;
      }

      public String getUserId(){
        return this.userId ;
      }

      public void setPassword (String password){
        this.password = password;
      }

      public String getPassword(){
        return this.password;
      }

        /**
         * Resets all properties to their default values.
         */
        public void reset(ActionMapping mapping, HttpServletRequest request) {
          this.userId = null;
          this.password = null;
        }

        /**
         * Validates the form.  Returns a list of action
         * Of course in a production environment, your rules would be far more strict than this.
         */
      public ActionErrors validate(
          ActionMapping mapping, HttpServletRequest request ) {
          ActionErrors errors = new ActionErrors();

          if( getUserId() == null || getUserId().length() < 1 ) {
            errors.add("userId",new ActionMessage("error.userid.required"));
          }
          if( getPassword() == null || getPassword().length() < 1 ) {
            errors.add("password",new ActionMessage("error.password.required"));
          }

          return errors;
      }

    }

[Category:Java](Category:Java "wikilink")