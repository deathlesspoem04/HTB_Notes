## Hack The Box Academy 

### Web Requests

#### HTTP (HyperText Transfer Protocol)

-> Consists of a client and a server 
-> Request -> Server -> Return Resource -> Client
-> Default Port for HTTP : 80

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


User -> URL in Browser -> DNS Server (Domain : IP) -> Browser -> (GET Request) IP : WebServer : Port -> Response to Browser (Output)


#### HTTPS (HyperText Transfer Protocol Secure)

One of the major drawbacks of HTTP is that all data is transferred in clear text, meaning anyone between the source and destination can perform a Man-in-the-Middle (MiTM) attack to view the transferred data.

If we attempt to log in to an insecure website while monitoring the network traffic using a graphical packet network protocol analyzer such as Wireshark, we can see that the login credentials can be intercepted in cleartext. 

These drawbacks gave rise to the HTTPS (HTTP Secure) protocol. When this protocol is enabled, all communication between the client (user accessing a web application via their web browser), and the webserver that hosts the web application, is encrypted. 

Websites that enforce HTTPS can be identified through `https://` in the URL.

-> Default Port: 433

![HTTPS_Flow](https://academy.hackthebox.eu/storage/modules/35/HTTPS_Flow.png)

URL -> HTTP Port 80 -> *Redirect* (301 Moved Permanently Response Code) -> HTTPS Port 433 -> Client (Browser) Sends a Packet -> Server sends a packet -> Key exchange -> Client verifies and sends another key -> Encrypted Connection Established


An attacker may be able to perform an HTTP downgrade attack, which downgrades HTTPS communication to HTTP

-> By setting up a man-in-the-middle (MITM) attack and proxying (passing) all traffic through the attacker's host without the user's knowledge. 

Successful downgrade attack would result in the cleartext transfer of HTTP data, which the attacker can log and later examine or manipulate for malicious purposes.