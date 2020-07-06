---
layout: post
title: "Advanced Web Security: WebSockets"
permalink: /adv-websockets
categories: Advanced_web_security
---

*The Advanced Web Security series looks beyond the OWASP Top 10 web application security risks. For the full list of articles in this series, visit [this page](./series/).*

When you are browsing the web, most of the data sent to your browser uses the HTTP protocol. WebSockets are a newer feature from HTML5 that does not use HTTP, and therefore they are often overlooked. Luckily, WebSockets are simpler than HTTP, so they are easier to check for common vulnerabilities.

### Observing WebSocket Traffic

If you are using a web proxy tool like Burp Suite or OWASP ZAP, WebSocket traffic is shown in a separate tab from where HTTP traffic is shown. Below are screenshots showing where to find this tab. Note that in ZAP, the tab might only appear when WebSocket traffic exists.

![OWASP ZAP WebSockets tab](/public/2020-07-06-websockets1.png)
*Figure 1: The OWASP ZAP WebSockets tab*

![Burp Suite WebSockets tab](/public/2020-07-06-websockets2.png)
*Figure 2: The Burp Suite WebSockets tab*

The website [http://websocket.org/echo.html](http://websocket.org/echo.html) can also be used to run a simple WebSocket connection test.

### Vulnerability #1: Unencrypted WebSockets
WebSockets do not use HTTP, but instead use their own protocol. WebSocket communications are sent to an address that starts with ws:// or wss://, similar to how the HTTP protocol uses http:// and https://. Communications to an address starting with ws:// are not encrypted, which is a security concern. Instead, communications should be sent to an address starting with wss://, which encrypts the traffic using TLS, just like HTTPS.

### Vulnerability #2: Sensitive data leak
WebSockets can reveal sensitive data that the server should not be sending to users. For example, WebSocket traffic may reveal internal server details, hidden features in the web application, or data about other user accounts (such as usernames). Leaked information may be a security concern in itself, but the information may also assist another attack elsewhere in the web application.

### Vulnerability #3: Insecure authentication
The WebSocket protocol does not implement authentication. If the previous sentence does not sound a warning alarm in your mind, it should! The lack of built-in protocol-level authentication means the web application developer must make decisions about how to authenticate WebSocket connection requests, and custom authentication solutions often have vulnerabilities. The authentication process for creating new WebSocket connections should always be tested for vulnerabilities. The server may allow WebSocket connections without valid tokens, with a username that does not match the current token, or other authentication implementation errors.

### Vulnerability #4: Cross Site WebSocket Hijacking (CSWSH)
The same-origin policy is a security feature that websites use to prevent Cross-Site Request Forgery (CSRF). However, WebSockets are not protected by the same-origin policy. The server must protect WebSocket connection requests against a CSRF type of attack by using 1. a CSRF token for each WebSocket connection request and 2. the “Origin” header in the WebSocket connection request. If these solutions are not implemented, a Cross Site WebSocket Hijacking (CSWSH) vulnerability may exist. This can be a serious vulnerability, as [this $12,500 bug bounty](https://ysamm.com/?p=363) shows.

### Vulnerability #5: Conventional risks
WebSockets can provide another chance to test other conventional attacks. XSS, SQLi, IDOR, and other vulnerabilities may be exploited using WebSockets. Exploiting these vulnerabilities using WebSockets requires knowledge of these other risks, and therefore may take time and understanding to fully test. Understanding the data that is being transmitted over WebSockets is a key to exploiting these vulnerabilities.

### Vulnerability #6: Reverse proxy bypass
This may be the newest WebSocket vulnerability in this list. Mikhail Egorov outlined this vulnerability at Hacktivity 2019, and the end result is that an attacker can communicate with private server resources that should not normally be accessible to users. This can be done by modifying HTTP request headers in a WebSocket connection request to unexpected values, such by setting the Sec-WebSocket-Version header to a four digit number. It is also possible to add the “Upgrade: websocket” request normal HTTP requests to check if the server treats the request as a WebSocket connection request. Based on Mikhail’s initial findings, only the Envoy proxy (version 1.8.0 and before) and the Varnish proxy were found to be vulnerable. I expect more research like this will be done soon and reveal further findings.

### References
CSWSH introduction: [https://www.christian-schneider.net/CrossSiteWebSocketHijacking.html](https://www.christian-schneider.net/CrossSiteWebSocketHijacking.html)  
Portswigger Web Academy WebSocket labs: [https://portswigger.net/web-security/websockets](https://portswigger.net/web-security/websockets)  
Site that allows simple WebSocket connection test: [http://websocket.org/echo.html](http://websocket.org/echo.html)  
Mikhail Egorov’s conference talk on WebSocket security: [https://www.youtube.com/watch?v=gANzRo7UHt8](https://www.youtube.com/watch?v=gANzRo7UHt8)
