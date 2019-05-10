## Author

[Arshan Dabirsiaghi](http://i8jesus.com)

## The Problem

Anecdotally, most application security engineers could tell you that the
state of auditing and logging in web applications today is fairly poor.
This is due to a number of issues:

1.  Security-relevant events don't get logged
2.  The information contained within those log messages is incomplete
3.  It's difficult to analyze, filter and generally reconstruct an
    attack because messages are spread around various log levels

The goal of this page is to let you know how to fix the last item in the
list. A <i>Security</i> log level can help an incident response team
filter out security-related messages and reconstruct an attack. There
are two files here, **SecurityLevel.java** and **log4j.xml**. To add
this level to your project, simply add **SecurityLevel.java** to your
classpath. If you want to execute the test case, add the **log4j.xml**
file to your classpath. If you're getting a "No appenders found" error,
make sure there is a **log4j.xml** or **log4j.properties** file on your
classpath, because log4j can't find either.

## The Java Code: **SecurityLevel.java**

<code>

    /**
     * This is a custom {@link org.apache.log4j.Level} for security logging. Nods to Jaikiran Pai for
     * his example code {@linkplain http://jaikiran.wordpress.com/2006/07/12/create-your-own-logging-level-in-log4j/} of which
     * this is a total bite. Also, thanks to Roman Hustad for helped me realize I should stop bitching about Log4j
     * not having one of these and make it myself.
     *
     * If you're getting a "No appenders could be found" error, make sure your log4j.xml or log4j.properties file
     * is on the classpath, because it isn't.
     *
     * @author Arshan Dabirsiaghi
     *
     */

    package org.owasp.logging;

    import org.apache.log4j.Level;
    import org.apache.log4j.Logger;


    public class SecurityLevel extends Level {

            /**
             * Value of security level. This value is slightly higher than {@link org.apache.log4j.Priority#INFO_INT}.
             */
            public static final int SECURITY_LEVEL_INT = Level.INFO_INT + 1;

            /**
             * {@link Level} representing my log level
             */
            public static final Level SECURITY = new SecurityLevel(SECURITY_LEVEL_INT,"SECURITY",7);

            private static final String SECURITY_MSG = "SECURITY";

            /**
             * Default constructor.
             */
            protected SecurityLevel(int arg0, String arg1, int arg2) {
                super(arg0, arg1, arg2);

            }

            /**
             * Checks whether <code>sArg</code> is "SECURITY" level. If yes then returns {@link SecurityLevel#SECURITY},
             * else calls {@link SecurityLevel#toLevel(String, Level)} passing it {@link Level#DEBUG} as the defaultLevel
             *
             * @see Level#toLevel(java.lang.String)
             * @see Level#toLevel(java.lang.String, org.apache.log4j.Level)
             *
             */
            public static Level toLevel(String sArg) {
                if (sArg != null && sArg.toUpperCase().equals(SECURITY_MSG)) {
                    return SECURITY;
                }
                return (Level) toLevel(sArg, Level.DEBUG);
            }

            /**
             * Checks whether <code>val</code> is {@link SecurityLevel#SECURITY_LEVEL_INT}. If yes then returns {@link SecurityLevel#SECURITY},
             * else calls {@link SecurityLevel#toLevel(int, Level)} passing it {@link Level#DEBUG} as the defaultLevel
             *
             * @see Level#toLevel(int)
             * @see Level#toLevel(int, org.apache.log4j.Level)
             *
             */
            public static Level toLevel(int val) {
                if (val == SECURITY_LEVEL_INT) {
                    return SECURITY;
                }
                return (Level) toLevel(val, Level.DEBUG);
            }

            /**
             * Checks whether <code>val</code> is {@link SecurityLevel#SECURITY_LEVEL_INT}. If yes then returns {@link SecurityLevel#SECURITY},
             * else calls {@link Level#toLevel(int, org.apache.log4j.Level)}
             *
             * @see Level#toLevel(int, org.apache.log4j.Level)
             */
            public static Level toLevel(int val, Level defaultLevel) {
                if (val == SECURITY_LEVEL_INT) {
                    return SECURITY;
                }
                return Level.toLevel(val,defaultLevel);
            }

            /**
             * Checks whether <code>sArg</code> is "SECURITY" level. If yes then returns {@link SecurityLevel#SECURITY},
             * else calls {@link Level#toLevel(java.lang.String, org.apache.log4j.Level)}
             *
             * @see Level#toLevel(java.lang.String, org.apache.log4j.Level)
             */
            public static Level toLevel(String sArg, Level defaultLevel) {
            if(sArg != null && sArg.toUpperCase().equals(SECURITY_MSG)) {
                return SECURITY;
            }
            return Level.toLevel(sArg,defaultLevel);
         }

         public static void main(String[] args) {

             Logger logger = Logger.getLogger(SecurityLevel.class.getName());

             logger.log(SecurityLevel.SECURITY,"This is a SECURITY level message");
             System.out.println("Wrote the log with my security level");

             logger.log(Level.DEBUG ,"I am a debug message");
             System.out.println("Wrote the log with debug level");

         }
    }

</code>

## Example **log4j.xml** file (optional)

<code>

    <?xml version="1.0" encoding="UTF-8"?>

    <!DOCTYPE log4j:configuration SYSTEM "log4j.dtd">

    <log4j:configuration xmlns:log4j="http://jakarta.apache.org/log4j/" debug="false">

    <!-- ============================== -->
    <!-- Append messages to the console -->
    <!-- ============================== -->

    <appender name="CONSOLE" class="org.apache.log4j.ConsoleAppender">

        <param name="Target" value="System.out"/>
        <param name="Threshold" value="TRACE"/>

        <layout class="org.apache.log4j.PatternLayout">

        <!-- The default pattern: Date Priority [Category] Messagen -->

        <param name="ConversionPattern" value="%d{ISO8601} %-5p [%c{1}] %m%n"/>

    </layout>

    </appender>

    <!-- ======================= -->
    <!-- Setup the Root category -->
    <!-- ======================= -->

    <root>

        <appender-ref ref="CONSOLE"/>

    </root>

    </log4j:configuration>

</code>

[Category:How_To](Category:How_To "wikilink")