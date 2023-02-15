- In a DHCP starvation attack, an attacker floods the DHCP server by sending a large number of DHCP requests and uses all available IP addresses that the DHCP server can issue. As a result, the server cannot issue any more IP addresses, leading to a Denial-of-Service (DoS) attack. Because of this issue, valid users cannot obtain or renew their IP addresses, and thus fail to access their network. This attack can be performed by using various tools such as Yersinia and Hyenae.

- Yersinia is a network tool designed to take advantage of weaknesses in different network protocols such as DHCP. It pretends to be a solid framework for analyzing and testing the deployed networks and systems.

- Open Terminal (yersinia works only in maximized terminal)
	> yersinia -I (**-I**: Starts an interactive ncurses session)
	
	- Press **F2** to select DHCP mode. In DHCP mode, **STP Fields** in the lower section of the window change to **DHCP Fields**.
	- Press **x** to list available attack options.
	- The **Attack Panel** window appears; press **1** to start a DHCP starvation attack.
	- **Yersinia** starts sending DHCP packets to the network adapter and all active machines in the local network.
		- If you are using multiple targets, you will observe the same packets on all target machines.
	- After a few seconds, press **q** to stop the attack and terminate Yersinia.
