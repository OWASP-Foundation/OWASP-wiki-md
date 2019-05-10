is there any perofrmance issues if more than 250+ users are hitting with
webscarab proxyserver. pls share your expereinces..thanx Rajan

Hi, I have a query regarding Webscarab Proxy setup on Windows machine. I
have one machine which is acting as Proxy server whose ip is
(10.10.10.100) and is listening on port 8080. I have another machine
which i am using as a client.In the browser settings Tools-\>Internet
Options -\>Connections -\>LAN settings I have checked to Use Proxy
serevr (have given my Proxy server IP 10.10.10.100 and port 8080 I have
installed Webscarab in my client machine . In the Webscarbs menu
Tools-\>Proxies have given \[10.10.10.100 and port 8080\]. I am starting
Webgoat project but am not able to see and http requests intercepted in
webscarab . So my Webscarab is not set properly. I know the default port
of Webscarab is 8008. So how should i dop the set up to solve this
problem. Thanks, Madhavi

  -
    To all who have this problem:
    1.  It looks like in the setup above there is nothing that tells the
        browser to send any requests through WebScarab. In Internet
        Explorer's "LAN Settings" dialog, declare 127.0.0.1:8008 (the
        local WebScarab's listening port) as proxy.
    2.  With the setup so far, WebGoat can be accessed and the traffic
        goes Internet Explorer-\>WebScarab-\>proxy server-\>WebGoat.
        However, WebGoat is probably installed on the client machine, so
        it might seem that it can be accessed both at 127.0.0.1 and at
        10.x.y.z or the associated host names, "localhost" for the first
        and whatever for the second. If the 10.x.y.z way is used, it
        should always work.
    3.  I am not sure that it makes sense to use the proxy server
        (10.10.10.100) for accessing WebGoat, the way WebScarab does in
        the description. It would make sense, for example, if the
        machine with WebGoat was only accessible by going through the
        proxy server or if even traffic to WebScarab had to go through
        the proxy server for logging. In order to avoid the proxy
        server, the "No Proxy" field in WebScarab's Tools-\>Proxies
        dialog should be used. I think it accepts the host names that
        need to be exempt from being accessed through the proxy server.
    \--[Thomas Herlea](User:Thomas_Herlea "wikilink") 11:46, 13
    September 2010 (UTC)