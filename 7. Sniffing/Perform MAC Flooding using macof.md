- MAC flooding is a technique used to compromise the security of network switches that connect network segments or network devices. Attackers use the MAC flooding technique to force a switch to act as a hub, so they can easily sniff the traffic.

- macof is a Unix and Linux tool that is a part of the dsniff collection. It floods the local network with random MAC addresses and IP addresses, causing some switches to fail and open in repeating mode, thereby facilitating sniffing. This tool floods the switch’s CAM tables (131,000 per minute) by sending forged MAC entries. When the MAC table fills up, the switch converts to a hub-like operation where an attacker can monitor the data being broadcast.
- Open Terminal
	> macof -i eth0 -n 10
	- **-i**: specifies the interface and **-n**: specifies the number of packets to be sent (here, **10**)

	> macof -i eth0 -d #targetip (to target a single system)
	- **-d**: Specifies the destination IP address
	- This command will start flooding the CAM table with random MAC addresses.