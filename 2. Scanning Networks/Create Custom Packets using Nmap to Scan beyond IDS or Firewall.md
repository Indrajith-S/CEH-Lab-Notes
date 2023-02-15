- Using Namp- Zenmap GUI
	> nmap #ip --data 0xdeadbeef

	- Nmap uses --data (hex string) (here, **0xdeadbeef**) to send the binary data (o’s and 1’s) as payloads in the sent packets to scan beyond firewalls.

	> nmap #ip --data-string “Ph34r my l33t skills
	
	- Nmap uses **--data-string (string)** (here, “**Ph34r my l33t skills**”) to send a regular string as payloads in the sent packets to the target machine for scanning beyond the firewall.

	> nmap --data-length 5 #ip 
	
	- Nmap uses **--data-length (len)**(here, **5**) to append the number of random data bytes to most of the packets sent without any protocol-specific payloads.

	 > nmap --randomize-hosts #ip 
	 
	 - Nmap uses **--randomize-hosts** to scan the number of hosts in the target network in random order to scan the intended target that is beyond the firewall.

	> nmap --badsum #ip 

	- Nmap uses **--badsum** to send the packets with bad or bogus TCP/UPD checksums to the intended target to avoid certain firewall rulesets.
	