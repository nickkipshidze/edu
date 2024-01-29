## Protocols
Set of rules and messages that form an internet standard.

#### ARP
Address Resolution Protocol

Resolves IP to MAC mappings. ARP requests / ARP responses - RFC 826.

#### FTP
File Transfer Protocol

Allows a client and the server to send and receive files form each other. The FTP "conversation" goes like this: The client would send the `RETR` command which stands for retrieve and ask for a particular file and this would prompt the server to respond with that file.

#### SMTP
Simple Mail Transfer Protocol

The client will sent the `HELO` command to an SMTP server, the SMTP server will then respond with a response code of 250 and now the client and the server can exchange emails with one another.

#### HTTP
Hyper Text Transfer Protocol

This is the protocol you're using anytime you're communicating with a web server. Web servers host many web sites written in HTML. HTML pages are exchanged using HTTP. When you browse to `site.com` your client/browser is sending a `GET` request to the web server and the web server will respond with a `200 OK` message and then provide the website you are asking for.

#### SSL/TLS
Secure Sockets Layer
Transport Layer Security

Allows the client and the server to build a secure tunnel between themselves and then they can do that HTTP conversation within that tunnel. That process is known as HTTPS.

#### HTTPS
Hyper Text Transfer Protocol Secured (with SSL/TLS)

#### DNS
Domain Name System

DNS will use a DNS server to convert a domain name into an IP address. When you type in a website into your browser, your browser is first going to make a request to a DNS server, asking for the IP address of the website that you just typed into your browser and then the DNS server will provide an IP address and this will now allow your host to make a request to the actual web server IP address even though you never provided the website IP address itself. Your computer was able to figure it out automatically by using the DNS protocol.

DNS is also what makes email possible. If I were to ask you for your email you'd probably give me something that looked like this `nick@email.com` and not the actual IP address of your email server. DNS would resolve this `email.com -> 47.208.5.20` into your actual mail service IP address and now your client can actually send mail to the mail server.

#### DHCP
Dynamic Host Configuration Protocol

DHCP allows a DHCP server to provide IP address, a mask, a default gateway and a DNS server for any client. This is actually what happens every time you connect to a new network. Your host will send a DHCP `discover` message to discover the DHCP server and then the DHCP server will provide these four things in response back to the client: IP, SM, DG, DNS. Then your client has everything it needs in order to speak to the internet.

#### NTP
Network Time Protocol

NTP is a crucial aspect of cyber security, as it helps synchronizing the clocks of computer systems and other devices within a network. Proper time synchronization is vital for various functions, including authentication, logging, and ensuring the accuracy of digital signatures.