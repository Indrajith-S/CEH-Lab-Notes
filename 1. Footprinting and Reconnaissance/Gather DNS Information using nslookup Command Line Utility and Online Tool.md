- Using nslookup
	> nslookup
	> set type= a

	- Setting the type as “**a”** configures nslookup to query for the IP address of a given domain.
	> www.certifiedhacker.com
	
	- The first two lines in the result are:    
	    Server: **dns.google** and Address: **8.8.8.8**    
		This specifies that the result was directed to the default server hosted on the local machine (**Windows 10**) that resolves your requested domain.
    
	- Thus, if the response is coming from your local machine’s server (Google), but not the server that legitimately hosts the domain **www.certifiedhacker.com**; it is considered to be a non-authoritative answer. Here, the IP address of the target domain **www.certifiedhacker.com** is **162.241.216.11**.
	- Since the result returned is non-authoritative, you need to obtain the domain's authoritative name server.
	> set type= cname
	
	- The CNAME lookup is done directly against the domain's authoritative name server and lists the CNAME records for a domain.
	> www.certifiedhacker.com
	
	- This returns the domain’s authoritative name server (**ns1.bluehost.com**), along with the mail server address (**dnsadmin.box5331.bluehost.com**), as shown in the screenshot.

	> set type= a
	> ns1.bluehost.com

	- The authoritative name server stores the records associated with the domain. So, if an attacker can determine the authoritative name server (primary name server) and obtain its associated IP address, he/she might attempt to exploit the server to perform attacks such as DoS, DDoS, URL Redirection, etc.