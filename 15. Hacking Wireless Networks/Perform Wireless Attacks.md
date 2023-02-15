- After performing the discovery, mapping, and analysis of the target wireless network, you have gathered enough information to launch an attack. You should now carry out various types of attacks on the target network, including Wi-Fi encryption cracking (WEP, WPA, and WPA2), fragmentation, MAC spoofing, DoS, and ARP poisoning attacks.

- WEP encryption is used for wireless networks, but it has several exploitable vulnerabilities. When seeking to protect a wireless network, the first step is always to change your SSID from the default before you actually connect the wireless router to the access point. Moreover, if an SSID broadcast is not disabled on an access point, ensure that you do not use a DHCP server, which would automatically assign IP addresses to wireless clients. This is because war-driving tools can easily detect your internal IP address.

- As an ethical hacker and pen tester of an organization, you must test its wireless security, exploit WEP flaws, and crack the network’s access point keys.

- There are several different types of Wi-Fi attacks that attackers use to eavesdrop on wireless network connections in order to obtain sensitive information such as passwords, banking credentials, and medical records, as well as to spread malware.

- These include:

	- **Fragmentation attack**: When successful, such attacks can obtain 1,500 bytes of PRGA (pseudo random generation algorithm)
	    
	- **MAC spoofing attack**: The attacker changes their MAC address to that of an authenticated user in order to bypass the access point’s MAC-filtering configuration
	    
	- **Disassociation attack**: The attacker makes the victim unavailable to other wireless devices by destroying the connectivity between the access point and client
	    
	- **Deauthentication attack**: The attacker floods station(s) with forged deauthentication packets to disconnect users from an access point
	    
	- **Man-in-the-middle attack**: An active Internet attack in which the attacker attempts to intercept, read, or alter information between two computers
	    
	- **Wireless ARP poisoning attack**: An attack technique that exploits the lack of a verification mechanism in the ARP protocol by corrupting the ARP cache maintained by the OS in order to associate the attacker’s MAC address with the target host
	    
	- **Rogue access points**: Wireless access points that an attacker installs on a network without authorization and that are not under the management of the network administrator
	    
	- **Evil twin**: A fraudulent wireless access point that pretends to be a legitimate access point by imitating another network name
    
	- **Wi-Jacking attack**: A method used by attackers to gain access to an enormous number of wireless networks



### Crack a WEP network using Aircrack-ng

- Aircrack-ng is a network software suite consisting of a detector, packet sniffer, WEP, and WPA/WPA2-PSK cracker and analysis tool for 802.11 wireless networks. The program runs on both Linux and Windows.

- In this task, we will use the Aircrack-ng suite to crack the WEP encryption of a network.
	- In order to capture wireless traffic, a wireless adapter is required and using an adapter in the iLabs environment is not possible, therefore, in this lab, we are using a sample capture file (**WEPcrack-01.cap**) to crack WEP key.

- Open Terminal
	> aircrack-ng '/home/attacker/Desktop/Sample Captures/WEPcrack-01.cap'
	- By issuing the above command **aircrack-ng** will crack the WEP key of the **CEHLabs**.
	- In real-life attacks, attackers will use this key to connect to the access point and join the target network. Once they enter the target network, they can use scanning tools to scan for open devices, perform a vulnerability analysis, and then start exploiting any vulnerabilities they find.



### Crack a WPA2 Network using Aircrack-ng

- WPA2 is an upgrade to WPA; it includes mandatory support for Counter Mode with Cipher Block Chaining Message Authentication Code Protocol (CCMP), an AES-based encryption protocol with strong security. WPA2 has two modes of operation: WPA2-Personal and WPA2-Enterprise. Despite being stronger than both WEP and WPA, the WPA2 encryption method can also be cracked using various techniques and tools.

- In this task, we will use the Aircrack-ng suite to crack a WPA2 network.
	- Before starting this task, you need to configure your access point router (**CEHLabs**) to work in WPA2-PSK (Pre-Shared Key) encryption mode. To do so, navigate to the router’s default IP address and change the authentication mode from WPA to WPA2-PSK, with the password as **password1**.
	- In order to capture wireless traffic, a wireless adapter is required and using an adapter in the iLabs environment is not possible, therefore, in this lab, we are using a sample capture file (**WPA2crack-01.cap**) to crack WPA key.



- Open Terminal
	> aircrack-ng -a2 -b #targetBSSID -w /home/attacker/Desktop/Wordlist/password.txt '/home/attacker/Desktop/Sample Captures/WPA2crack-01.cap' 
	
	- -   **-a** is the technique used to crack the handshake, **2**=WPA technique.
	-   **-b** refers to bssid; replace with the BSSID of the target router.
	-   **-w** stands for wordlist; provide the path to a wordlist.

- The result appears, showing the WPA handshake packet captured with airodump-ng. The target access point’s password is cracked and displayed in plain text next to the message **KEY FOUND!.
	- If the password is complex, aircrack-ng will take a long time to crack it.