- An Intrusion Detection System (IDS) and firewall are the security mechanisms intended to prevent an unauthorized person from accessing a network. However, even IDSs and firewalls have some security limitations. Firewalls and IDSs intend to avoid malicious traffic (packets) from entering into a network, but certain techniques can be used to send intended packets to the target and evade IDSs/firewalls.

- Techniques to evade IDS/firewall:

	- **Packet Fragmentation**: Send fragmented probe packets to the intended target, which re-assembles it after receiving all the fragments
	- **Source Routing**: Specifies the routing path for the malformed packet to reach the intended target
	- **Source Port Manipulation**: Manipulate the actual source port with the common source port to evade IDS/firewall
	- **IP Address Decoy**: Generate or manually specify IP addresses of the decoys so that the IDS/firewall cannot determine the actual IP address
	- **IP Address Spoofing**: Change source IP addresses so that the attack appears to be coming in as someone else
	- **Creating Custom Packets**: Send custom packets to scan the intended target beyond the firewalls
	- **Randomizing Host Order**: Scan the number of hosts in the target network in a random order to scan the intended target that is lying beyond the firewall
	-  **Sending Bad Checksums**: Send the packets with bad or bogus TCP/UPD checksums to the intended target
	-  **Proxy Servers**: Use a chain of proxy servers to hide the actual source of a scan and evade certain IDS/firewall restrictions
	-  **Anonymizers**: Use anonymizers that allow them to bypass Internet censors and evade certain IDS and firewall rules
- Open Nmap
	> nmap -f #ip
	
	- **-f** switch is used to split the IP packet into tiny fragment packets.
	- Packet fragmentation refers to the splitting of a probe packet into several smaller packets (fragments) while sending it to a network. When these packets reach a host, IDSs and firewalls behind the host generally queue all of them and process them one by one. However, since this method of processing involves greater CPU consumption as well as network resources, the configuration of most of IDSs makes it skip fragmented packets during port scans.

	> nmap -g #ip
	
	- In this command, you can use the **-g** or **--source-port** option to perform source port manipulation.
	- Source port manipulation refers to manipulating actual port numbers with common port numbers to evade IDS/firewall: this is useful when the firewall is configured to allow packets from well-known ports like HTTP, DNS, FTP, etc.

	> nmap -D RND:10 #ip

	- In this command, **-D**: performs a decoy scan and **RND**: generates a random and non-reserved IP addresses.
	- The IP address decoy technique refers to generating or manually specifying IP addresses of the decoys to evade IDS/firewall. This technique makes it difficult for the IDS/firewall to determine which IP address was actually scanning the network and which IP addresses were decoys. By using this command, Nmap automatically generates a random number of decoys for the scan and randomly positions the real IP address between the decoy IP addresses.