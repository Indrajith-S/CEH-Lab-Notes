- An attacker can obtain usernames and passwords using various techniques or by capturing data packets. By merely capturing enough packets, attackers can extract a target’s username and password if the victim authenticates themselves in public networks, especially on unsecured websites. Once a password is hacked, an attacker can use the password to interfere with the victim’s accounts such as by logging into the victim’s email account, logging onto PayPal and draining the victim’s bank account, or even change the password.

- As a preventive measure, an organization’s administrator should advice employees not to provide sensitive information while in public networks without HTTPS connections. VPN and SSH tunneling must be used to secure the network connection. An expert ethical hacker and penetration tester (hereafter, pen tester) must have sound knowledge of sniffing, network protocols and their topology, TCP and UDP services, routing tables, remote access (SSH or VPN), authentication mechanisms, and encryption techniques.

- Another effective method for obtaining usernames and passwords is by using Cain & Abel to perform MITM attacks.

- An MITM attack is used to intrude into an existing connection between systems and to intercept the messages being exchanged. Using various techniques, attackers split the TCP connection into two connections—a client-to-attacker connection and an attacker-to-server connection. After the successful interception of the TCP connection, the attacker can read, modify, and insert fraudulent data into the intercepted communication.

- MITM attacks are varied and can be carried out on a switched LAN. MITM attacks can be performed using various tools such as Cain & Abel.

- Cain & Abel is a password recovery tool that allows the recovery of passwords by sniffing the network and cracking encrypted passwords. The ARP poisoning feature of the Cain & Abel tool involves sending free spoofed ARPs to the network’s host victims. This spoofed ARP can make it easier to attack a middleman.

- Open Cain & Abel
	- Click **Configure** from the menu bar to configure an ethernet card.
	- The **Configuration Dialog** window appears. By default, the **Sniffer** tab is selected. Ensure that the **Adapter** associated with the **IP address** of the machine is selected; then, click **OK**.
	- Click the **Start/Stop Sniffer** icon on the toolbar to begin sniffing.
	- Now, click the **Sniffer** tab.
	- Click the plus (**+**) icon or right-click in the window and select **Scan MAC Addresses** to scan the network for hosts.
	- The **MAC Address Scanner** window appears. Check the **All hosts in my subnet** radio button and select the **All Tests** checkbox; then, click **OK**.
	- Cain & Abel starts scanning for MAC addresses and lists all those found.
	- After completing the scan, a list of all active IP addresses along with their corresponding MAC addresses is displayed.
	- Now, click the **APR** tab at the bottom of the window.
	- APR options appear in the left-hand pane. Click anywhere on the topmost section in the right-hand pane to activate the plus (**+**) icon.
	- Click the plus (**+**) icon, a **New ARP Poison Routing** window appears, from which we can add IPs to listen to traffic.
	- To monitor the traffic between two systems (here, **Windows 10** and **Windows Server 2016**), click to select **10.10.10.10** (Windows 10) from the left-hand pane and **10.10.10.16** (**Windows Server 2016**) from the right-hand pane; click **OK**.
	- Click to select the created target IP address scan displayed in the **Configuration / Routes Packets** tab.
	- Click on the **Start/Stop APR** icon to start capturing ARP packets.
	- Now lets say an ftp connection is initiated between 10.10.10.16 and 10.10.10.10, using creds for ftp, then all the passwords are spoofed by the host.
	- Click the **Passwords** tab from the bottom of the window. Click **FTP** from the left-hand pane to view the sniffed password for **ftp 10.10.10.10.
		- In real-time, attackers use the ARP poisoning technique to perform sniffing on the target network. Using this method, attackers can steal sensitive information, prevent network and web access, and perform DoS and MITM attacks.