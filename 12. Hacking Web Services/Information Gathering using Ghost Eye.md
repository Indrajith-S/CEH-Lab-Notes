- Ghost Eye is an information-gathering tool written in Python 3. To run, Ghost Eye only needs a domain or IP. Ghost Eye can work with any Linux distros if they support Python 3.

- Ghost Eye gathers information such as Whois lookup, DNS lookup, EtherApe, Nmap port scan, HTTP header grabber, Clickjacking test, Robots.txt scanner, Link grabber, IP location finder, and traceroute.
- Open Terminal
	> sudo su
	> cd
	> cd ghost_eye
	> pip3 install -r requirements.txt
	> python3 ghost_eye.py (To launch ghost eye)
	
	- The Ghost Eye - Information Gathering Tool options appear.
	> 1 (to perform a Whois Lookup)
	> nadasurabhi.org
	- Scroll up to see the certifiedhacker.com result. In the result, observe the complete information of the certifiedhacker.com domain such as Domain Name, Registry Domain ID, Registrar WHOIS Server, Registrar URL, and Updated Date.

	> 6 (to perform Clickjacking test)
	> nadasurabhi.org
	
	- By performing this test, Ghost Eye will provide the complete architecture of the web server, and also reveal whether the domain is vulnerable to Clickjacking attacks or not.
	- Similarly, you can use the other tools available with Ghost Eye such as Nmap port scan, HTTP header grabber, link grabber, and Robots.txt scanner to gather information about the target web server.