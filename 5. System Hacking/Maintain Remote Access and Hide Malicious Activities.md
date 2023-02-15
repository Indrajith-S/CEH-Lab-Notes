- As a professional ethical hacker or pen tester, the next step after gaining access and escalating privileges on the target system is to maintain access for further exploitation on the target system.
- Now, you can remotely execute malicious applications such as keyloggers, spyware, backdoors, and other malicious programs to maintain access to the target system. You can hide malicious programs or files using methods such as rootkits, steganography, and NTFS data streams to maintain access to the target system.
- Maintaining access will help you identify security flaws in the target system and monitor the employees’ computer activities to check for any violation of company security policy. This will also help predict the effectiveness of additional security measures in strengthening and protecting information resources and systems from attack.


### User System Monitoring and Surveillance using Power Spy

- Power Spy is a computer activity monitoring software that allows you to secretly log all users on a PC while they are unaware. After the software is installed on the PC, you can remotely receive log reports on any device via email or FTP. You can check these reports as soon as you receive them or at any convenient time. You can also directly check logs using the log viewer on the monitored PC.
- There are several key points to keep in mind:

	-   This lab only works if the target machine is turned **ON**
	-   You have learned how to escalate privileges in the earlier lab and will use the same technique here to escalate privileges, and then dump the password hashes
	-   On obtaining the hashes, you will use a password-cracking application such as Responder to obtain plain text passwords
	-   Once you have the passwords, establish a Remote Desktop Connection as the attacker; install keylogger tools (such as Power Spy) and leave them in stealth mode
	-   The next task will be to log on to the machine as a legitimate user, and, as the victim, perform user activities as though you are unaware of the application tracking your activities
	-   After completing some activities, you will again establish a **Remote Desktop Connection** as an attacker, bring the application out of stealth mode, and monitor the activities performed on the machine by the victim (you)



- In the host machine, open Remote Desktop Connection.
- The **Remote Desktop Connection** window appears. In the **Computer** field, type the target system’s IP address (here, **10.10.10.16** [**Windows Server 2016**]) and click **Connect**.
- Enter the credentials
	- You cannot access the target machine remotely if the system is off. This process is possible only if the machine is turned on.
- Minimize the **Remote Desktop Connection** window.
- Navigate to **Spyware\General Spyware\Power Spy** and copy **setup.exe**.
- Switch to the **Remote Desktop Connection** window and paste the **setup.exe** file on the target system’s **Desktop**.
- Double-click the **setup.exe** file.
- After the installation completes, the **Completing the Power Spy Setup Wizard** appears; click **Finish**. The **Run as Administrator** window appears; click **Run**.
- The **Setup login password** window appears. Enter the password **test@123** in the **New password** and **Confirm password** fields; click **Submit**.
- Click the **Start monitoring** option from the right-pane.
- Click on **Stealth Mode** from the right-pane.
	- Stealth mode runs Power Spy on the computer completely invisibly.
	- To unhide Power Spy, use the **Ctrl+Alt+X** keys together on your PC keyboard.
- Delete the Power Spy installation setup (**setup.exe**) from **Desktop**.
- Close the **Remote Desktop Connection** by clicking on the close icon (**X**).
- Now whatever the victim does on the target machine the remote desktop connection logs it.
- Now open remote desktop connection again, enter #targetip, click connect and enter the creds.
- The **Power Spy Control Panel** window appears. Click on **Stop monitoring** to stop monitoring the user activities.
- Click **Applications executed** from the options to check the applications running on the target system.
- A window appears, showing the applications running on the target system.
- Similarly, you can click on other options such as **Websites Visited**, **Windows Opened**, **Clipboard**, and **Event History** to check other detailed information.
	- Using this method, an attacker might attempt to install keyloggers and thereby gain information related to the websites visited by the victim, keystrokes, password details, and other information.


### User System Monitoring and Surveillance using Spytech SpyAgent

- Spytech SpyAgent is a powerful piece of computer spy software that allows you to monitor everything users do on a computer—in complete stealth mode. SpyAgent provides a large array of essential computer monitoring features as well as website, application, and chat-client blocking, lockdown scheduling, and the remote delivery of logs via email or FTP.
- Follow the same steps for the above spyware for this as well, except we will be dealing with the syptech sypAgent tool here and follow the necessary steps.
