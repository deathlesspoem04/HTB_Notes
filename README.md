## Hack The Box Academy 

### Web Requests

#### HTTP (HyperText Transfer Protocol)

&#8594; Consists of a client and a server 
&#8594; Request &#8594; Server &#8594; Return Resource &#8594; Client
&#8594; Default Port for HTTP : 80

![url_structure](https://academy.hackthebox.eu/storage/modules/35/url_structure.png)

**Scheme**

This is used to identify the protocol being accessed by the client. This is usually `http` or `https`.

**User Info**

This is an optional component that contains credentials in the form `username:password`, which is used to authenticate to the host.

**Host**

The host signifies the resource location. This can be a hostname or an IP address. A colon separates a host and port.

**Port**

URLs without a port specified point to the default port 80. If the HTTP server port isn't running on port 80, it can be specified in the URL.

**Path**

This points to the resource being accessed, which can be a file or a folder. If there no path specified, the server returns the default index document hosted by it (for example, index.html).

**Query String**

The query string is preceded by a question mark (?). This is another optional component that is used to pass information to the resource. A query string consists of a parameter and a value. In the example above, the parameter is `login`, and its `value` is true. There can be multiple parameters separated by an ampersand (&).

**Fragments**

This is processed by browsers on the client-side to locate sections within the primary resource.


![HTTP_Flow](https://academy.hackthebox.eu/storage/modules/35/HTTP_Flow.png)


User &#8594; URL in Browser &#8594; DNS Server (Domain : IP) &#8594; Browser &#8594; (GET Request) IP : WebServer : Port &#8594; Response to Browser (Output)


#### HTTPS (HyperText Transfer Protocol Secure)

One of the major drawbacks of HTTP is that all data is transferred in clear text, meaning anyone between the source and destination can perform a Man-in-the-Middle (MiTM) attack to view the transferred data.

If we attempt to log in to an insecure website while monitoring the network traffic using a graphical packet network protocol analyzer such as Wireshark, we can see that the login credentials can be intercepted in cleartext. 

These drawbacks gave rise to the HTTPS (HTTP Secure) protocol. When this protocol is enabled, all communication between the client (user accessing a web application via their web browser), and the webserver that hosts the web application, is encrypted. 

Websites that enforce HTTPS can be identified through `https://` in the URL.

&#8594; Default Port: 433

![HTTPS_Flow](https://academy.hackthebox.eu/storage/modules/35/HTTPS_Flow.png)

URL &#8594; HTTP Port 80 &#8594; *Redirect* (301 Moved Permanently Response Code) &#8594; HTTPS Port 433 &#8594; Client (Browser) Sends a Packet &#8594; Server sends a packet &#8594; Key exchange &#8594; Client verifies and sends another key &#8594; Encrypted Connection Established


An attacker may be able to perform an HTTP downgrade attack, which downgrades HTTPS communication to HTTP

&#8594; By setting up a man-in-the-middle (MITM) attack and proxying (passing) all traffic through the attacker's host without the user's knowledge. 

Successful downgrade attack would result in the cleartext transfer of HTTP data, which the attacker can log and later examine or manipulate for malicious purposes.

#### Burp Suite

&#8594; It is a tool that acts as a *proxy server* and can be used to examine and modify the HTTP requests.
&#8594; It provides a proxy that can route traffic from the browser through the proxy and view the various requests and responses b/w the client and server.

BurpSuite &#8594; FoxyProxy &#8594; Intercept (Server Responses)

HTTP request, as seen from Burp:

![raw_request](https://academy.hackthebox.eu/storage/modules/35/raw_request.png)

**Method**

The first field stands for the HTTP method or verb, which specifies the type of action to perform.

**Path**

The second field is the path to the resource being accessed. This field can also be suffixed with a query string.

**Version**

The third and final field is used to denote the HTTP version.


HTTP Response:

![raw_response](https://academy.hackthebox.eu/storage/modules/35/raw_response.png)

