#### Scan a Target Network using Metasploit

> msfdb init
> service postgresql start
> msfconsole
> db_status

> nmap -Pn -sS -oX Test 10.10.10.0/24

- Here, we are scanning the whole subnet 10.10.10.0/24 for active hosts.

> db_import Test

- to import the Nmap results from the database.

> hosts

- to view the list of active hosts along with their MAC addresses, OS names, etc.

> services

- to receive a list of the services running on the active hosts.


- In addition to running Nmap, there are a variety of other port scanners that are available within the Metasploit framework to scan the target systems.
	> search portscan
	> use auxiliary/scanner/portscan/syn

	- We will use this module to perform an SYN scan against the target IP address range (**10.10.10.5-20**) to look for open port 80 through the eth0 interface.
	> set INTERFACE eth0
	> set PORTS 80
	> set RHOSTS 10.10.10.5-20
	> set THREADS 50
	> run
	
	- **PORTS**: specifies the ports to scan (e.g., 22-25, 80, 110-900), 
	- **RHOSTS**: specifies the target address range or CIDR identifier, and 
	- THREADS: specifies the number of concurrent threads (default 1).

	- Now, we will perform a TCP scan for open ports on the target systems.
		> use auxiliary/scanner/portscan/tcp
		> hosts -R
		
			- to automatically set this option with the discovered hosts present in our database. OR
		> set RHOSTS #ip 
		> run
		

	- To load an FTP module
		> use auxiliary/scanner/ftp/ftp_version
		> set RHOSTS #ip 
		> run
		> hosts
		
		- to view detailed information on active hosts in the target network.
		- You can further export this information to a CSV file.

		> back
		> hosts -o /root/Desktop/Metasploit_Scan_Results.csv
		
		- You can observe **Metasploit_Scan_Results.csv** file. This CSV file, contains detailed information on the active hosts in the target IP range.
		- This information can further be used to perform vulnerability analysis on the open services discovered in the target hosts.