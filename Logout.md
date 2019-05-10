## Status

Released on (mm/dd/yyyy) : 01/20/2012

## Objective of session logout process

Session logout have to objective to cancel conversation established
between the browser and the web server. We means here, by conversation,
several browser request and response that has been linked between them.

## Steps of session logout process

Logout is composed by 2 steps:

1.  Invalidate user session (indicate to web server that the session is
    not used anymore).
2.  Cancel cookie send by the web server to track user session (and also
    all cookies sent by web application, this, in order to have a global
    clean state).

## Code sample of session logout process

    package org.owasp.javaproject.logout;

    import java.io.IOException;
    import javax.servlet.ServletException;
    import javax.servlet.annotation.WebServlet;
    import javax.servlet.http.Cookie;
    import javax.servlet.http.HttpServlet;
    import javax.servlet.http.HttpServletRequest;
    import javax.servlet.http.HttpServletResponse;
    import javax.servlet.http.HttpSession;

    /**
     * Code sample showing how to perform a complete logout
     */
    @SuppressWarnings("serial")
    @WebServlet("/Logout")
    public class LogoutCodeSample extends HttpServlet {

        /**
         * {@inheritDoc}
         *
         * @see javax.servlet.http.HttpServlet#doPost(javax.servlet.http.HttpServletRequest,
         *      javax.servlet.http.HttpServletResponse)
         */
        @Override
        protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
            doGet(request, response);
        }

        /**
         * {@inheritDoc}
         *
         * @see HttpServlet#doGet(HttpServletRequest request, HttpServletResponse
         *      response)
         */
        @Override
        protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
            /*
             * First step : Invalidate user session
             */
            HttpSession session = request.getSession(false);
            if (session != null) {
                session.invalidate();
            }

            /*
             * Second step : Invalidate all cookies by, for each cookie received,
             * overwriting value and instructing browser to deletes it
             */
            Cookie[] cookies = request.getCookies();
            if (cookies != null && cookies.length > 0) {
                for (Cookie cookie : cookies) {
                    cookie.setValue("-");
                    cookie.setMaxAge(0);
                    response.addCookie(cookie);
                }
            }

        }

    }

[Category:Java](Category:Java "wikilink")