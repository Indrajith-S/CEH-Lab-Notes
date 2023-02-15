- Using Nmap- Zenmap GUI
	> nmap -sn -PR #ip 
	
	-PR to perform ARP Ping scan
	-sn disables port scan

	> nmap -sn -PU #ip
		
	-PU performs UDP scan

	> nmap -sn -PE #ip
		
	-PE performs ICMP Echo scan


- The ICMP ECHO ping sweep is used to determine the live hosts from a range of IP addresses by sending ICMP ECHO requests to multiple hosts. If a host is alive, it will return an ICMP ECHO reply.


- ICMP timestamp ping scan
    > nmap -sn -PP [target IP address]
    
    ICMP address mask ping scan
    
    > nmap -sn -PM [target IP address]
    
- TCP SYN Ping Scan: This technique sends empty TCP SYN packets to the target host, ACK response means that the host is active.
    
    > nmap -sn -PS [target IP address]
    
- TCP ACK Ping Scan: This technique sends empty TCP ACK packets to the target host; an RST response means that the host is active.
    
    > nmap -sn -PA [target IP address]
    
- IP Protocol Ping Scan: This technique sends different probe packets of different IP protocols to the target host, any response from any probe indicates that a host is active.
    
    > nmap -sn -PO [target IP address]