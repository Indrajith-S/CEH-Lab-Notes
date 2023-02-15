- After gathering required information about the target web server, the next task for an ethical hacker or pen tester is to attack the web server in order to test the target network’s web server security infrastructure. This requires knowledge of how to perform web server attacks.

- Attackers perform web server attacks with certain goals in mind. These goals may be technical or non-technical. For example, attackers may breach the security of the web server to steal sensitive information for financial gain, or merely for curiosity’s sake. The attacker tries all possible techniques to extract the necessary passwords, including password guessing, dictionary attacks, brute force attacks, hybrid attacks, pre-computed hashes, rule-based attacks, distributed network attacks, and rainbow attacks. The attacker needs patience, as some of these techniques are tedious and time-consuming. The attacker can also use automated tools such as Brutus and THC-Hydra, to crack web passwords.

- An ethical hacker or pen tester must test the company’s web server against various attacks and other vulnerabilities. It is important to find various ways to extend the security test by analyzing web servers and employing multiple testing techniques. This will help to predict the effectiveness of additional security measures for strengthening and protecting web servers of the organization.


### Crack FTP Credentials using a Dictionary Attack

- A dictionary or wordlist contains thousands of words that are used by password cracking tools to break into a password-protected system. An attacker may either manually crack a password by guessing it or use automated tools and techniques such as the dictionary method. Most password cracking techniques are successful, because of weak or easily guessable passwords.

- First, find the open FTP port using Nmap, and then perform a dictionary attack using the THC Hydra tool.

- First perform a Nmap scan to see if ftp port is open
- Open Terminal
	> sudo su
	> cd
	> nmap -p 21 #targetip 
	
	- if open,
	- check if it is hosted on the victim machine
	> ftp #targetip 
	- You will be prompted to enter user credentials. The need for credentials implies that an FTP server is hosted on the machine.
	- Now, to attempt to gain access to the FTP server, perform a dictionary attack using the THC Hydra tool.
	> hydra -L #Usernameswordlist.txt -P #Passwordswordlist.txt ftp:// #targetip 
	- Hydra tries various combinations of usernames and passwords (present in the **Usernames.txt** and **Passwords.txt** files) on the FTP server and outputs cracked usernames and passwords.
	- On completion of the password cracking, the **cracked credentials** appear.
	- Try to log in to the FTP server using one of the cracked username and password combinations.
		- Enter **help** to view all other commands that you can use through the FTP terminal.
