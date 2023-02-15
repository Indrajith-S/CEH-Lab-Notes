- Network/security administrators play a crucial role in creating security defenses within an organization. Though such defenses protect the machines in the network, there might still be an insider who may try to apply different evasion techniques to identify the services running on the target.

- In this scenario, consider an admin has written certain Windows Firewall rules to block your system from reaching one of the machines in the network. You will be taught to use Nmap in such a way that you can perform recon on the target using other active machines on the network and identify the services running on the machine along with their open ports.
- Open Terminal
	- We will now perform a **Ping Sweep** scan on the subnet to discover the live machines in the network.
	> nmap -sP 10.10.10.0/24
	
	> nmap -sI #zombieip #targetip (to perform a zombie scan)
	
	- You can perform a Zombie scan by choosing any of the IPs that are obtained in the ping sweep scan. In this lab, we are choosing **Windows Server 2019** as the Zombie.