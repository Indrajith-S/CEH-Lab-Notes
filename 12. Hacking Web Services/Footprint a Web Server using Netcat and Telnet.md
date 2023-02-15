- Netcat is a networking utility that reads and writes data across network connections, using the TCP/IP protocol. It is a reliable “back-end” tool used directly or driven by other programs and scripts. It is also a network debugging and exploration tool.

- **Telnet**
	- Telnet is a client-server network protocol. It is widely used on the Internet or LANs. It provides the login session for a user on the Internet. The single terminal attached to another computer emulates with Telnet. The primary security problems with Telnet are the following:

		-   It does not encrypt any data sent through the connection.  
		-   It lacks an authentication scheme.
    

	- Telnet helps users perform banner-grabbing attacks. It probes HTTP servers to determine the Server field in the HTTP response header.
- Open Terminal (Using Netcat)
	> nc -vv #targeturl 80
	- the netcat will display the hosting information of the provided domain.

	> GET / HTTP/1.0 (press enter twice after previous command displays "Trying to get #targetip ")
	- Netcat will perform the banner grabbing and gather information such as content type, last modified date, accept ranges, ETag, and server information.


- Open Terminal (Using Telnet)
	> telnet #targeturl 80 (Telnet will connect to the domain)
	> GET / HTTP/1.0 (press enter twice after previous command displays "Trying to get #targetip ")
	- Telnet will perform the banner grabbing and gather information such as content type, last modified date, accept ranges, ETag, and server information.
