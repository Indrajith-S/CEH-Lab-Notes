- Promiscuous mode allows a network device to intercept and read each network packet that arrives in its entirety. The sniffer toggles the NIC of a system to promiscuous mode, so that it listens to all data transmitted on its segment. A sniffer can constantly monitor all network traffic to a computer through the NIC by decoding the information encapsulated in the data packet. Promiscuous mode in the network can be detected using various tools.

- Here, we will use the Nmap Scripting Engine (NSE) and NetScan Tools Pro to check if a system on a local Ethernet has its network card in promiscuous mode.
- To check if system is in promiscuous mode, open nmap 
	>nmap --script=sniffer-detect #targetip 
	- If the result says **Likely in promiscuous mode** under the **Host script results** section, then it indicates that the target system is in promiscuous mode.
