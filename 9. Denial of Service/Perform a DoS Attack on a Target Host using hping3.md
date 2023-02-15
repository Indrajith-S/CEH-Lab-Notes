- hping3 is a command-line-oriented network scanning and packet crafting tool for the TCP/IP p rotocol that sends ICMP echo requests and supports TCP, UDP, ICMP, and raw-IP protocols.

- It performs network security auditing, firewall testing, manual path MTU discovery, advanced traceroute, remote OS fingerprinting, remote uptime guessing, TCP/IP stacks auditing, and other functions.

- Here, we will use the hping3 tool to perform DoS attacks such as SYN flooding, Ping of Death (PoD) attacks, and UDP application layer flood attacks on a target host.


#### Performing SYN flood attack using hping3
- Open Terminal
	> sudo su
	> hping3 -S #targetip -a #spoofip -p 22 --flood
	- **-S**: sets the SYN flag; **-a**: spoofs the IP address; **-p**: specifies the destination port; and **--flood**: sends a huge number of packets.
	- This command initiates the SYN flooding attack on the **Windows 10** machine. After a few seconds, press **Ctrl+C** to stop the SYN flooding of the target machine.
	- **hping3** floods the victim machine by sending bulk **SYN packets** and **overloading** the victim’s resources.


#### Performing Ping of Death (PoD) attack using hping3

- Open Terminal
	> hping3 -d 65538 -S -p 21 --flood #targetip 
	- **-d**: specifies data size; **-S**: sets the SYN flag; **-p**: specifies the destination port; and **--flood**: sends a huge number of packets.
	- This command initiates the PoD attack on the **Windows 10** machine.
	- In a PoD attack, the attacker tries to crash, freeze, or destabilize the targeted system or service by sending malformed or oversized packets using a simple ping command.
	- For example, the attacker sends a packet that has a size of 65,538 bytes to the target web server. This packet size exceeds the size limit prescribed by RFC 791 IP, which is 65,535 bytes. The receiving system’s reassembly process might cause the system to crash.
	- **hping3** floods the victim machine by sending bulk packets, and thereby overloading the victim’s resources.



#### Performing UDP Application layer flood attack using hping3

- We do this using NetBIOS port (139)
- we check if its open
- Open Terminal
	> nmap -p 139 #targetip 
	- Here, we will use NetBIOS port 139 to perform a UDP application layer flood attack.
	> hping3 -2 -p 139 --flood #targetip 
	- **-2**: specifies the UDP mode; **-p**: specifies the destination port; and **--flood**: sends a huge number of packets.
	- Here, we have used NetBIOS port 139 to perform a UDP application layer flood attack. Similarly, you can employ other application layer protocols to perform a UDP application layer flood attack on a target network.
	- Some of the UDP based application layer protocols that attackers can employ to flood target networks include:
		- **CharGEN** (Port 19)
		- **SNMPv2** (Port 161)
		- **QOTD** (Port 17)
		- **RPC** (Port 135)
		- **SSDP** (Port 1900)
		- **CLDAP** (Port 389)
		- **TFTP** (Port 69)
		- **NetBIOS** (Port 137,138,139)
		- **NTP** (Port 123)
		- **Quake Network Protocol** (Port 26000)
		- **VoIP** (Port 5060)

