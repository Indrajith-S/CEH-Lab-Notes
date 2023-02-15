- Session hijacking is very dangerous; it places the victim at risk of identity theft, fraud, and loss of sensitive information. All networks that use TCP/IP are vulnerable to different types of hijacking attacks. Moreover, these kinds of attacks are very difficult to detect, and often go unnoticed unless the attacker causes severe damage. However, following best practices can protect against session hijacking attacks.

- As a professional ethical hacker or penetration tester, it is very important that you have the required knowledge to detect session hijacking attacks and protect your organization’s system against them. Fortunately, there are various tools available that can help you to detect session hijacking attacks such as packet sniffers, IDSs, and SIEMs.
- There are two primary methods that can be used to detect session hijacking:

	- **Manual Method**: Involves using packet sniffing software such as Wireshark and SteelCentral Packet Analyzer to monitor session hijacking attacks; the packet sniffer captures packets being transferred across the network, which are then analyzed using various filtering tools.
	- **Automatic Method**: Involves using Intrusion Detection Systems (IDS) and Intrusion Prevention Systems (IPS) to monitor incoming network traffic; if a packet matches any of the attack signatures in the internal database, the IDS generates an alert, and the IPS blocks the traffic from entering the database.


### Detect Session Hijacking using Wireshark

- Wireshark allows you to capture and interactively browse the traffic running on a network. The tool uses WinPcap to capture packets, and so is only able to capture packets on networks that are supported by WinPcap. It captures live network traffic from Ethernet, IEEE 802.11, PPP/HDLC, ATM, Bluetooth, USB, Token Ring, Frame Relay, and FDDI networks. Security professionals can use Wireshark to monitor and detect session hijacking attempts.

- Here, we will use the Wireshark tool to detect session hijacking attacks manually on the target system.
- Open Wireshark in the target or victim system and double click on the interface.
- Now, we shall launch a session hijacking attack on the target machine using **bettercap**.
- Now as the host or attacker
	- Open Terminal
		> sudo su
		> cd
		> bettercap -iface eth0 (**-iface**: specifies the interface to bind to (in this example, **eth0**)
		
		> net.probe on (This module will send different types of probe packets to each IP in the current subnet for the **net.recon** module to detect them)
		
		> net.recon on (This module is responsible for periodically reading the system ARP table to detect new hosts on the network)
		- The net.recon module displays the detected active IP addresses in the network. In real-time, this module will start sniffing network packets.

	> net.sniff on (This module is responsible for performing sniffing on the network)
	
	- You can observe that bettercap starts sniffing network traffic on different machines in the network.
- Now in the victim machine, observe the huge number of **ARP packets** captured by the **Wireshark**.
	- bettercap sends several ARP broadcast requests to the hosts (or potentially active hosts). A high number of ARP requests indicates that the system at **10.10.10.13** (the attacker’s system in this task) is acting as a client for all the IP addresses in the subnet, which means that all the packets from the victim node (in this case, **10.10.10.10**) will first go to the host system (**10.10.10.13**), and then the gateway. Similarly, any packet destined for the victim node is first forwarded from the gateway to the host system, and then from the host system to the victim node.
