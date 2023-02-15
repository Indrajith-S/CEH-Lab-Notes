- Open terminal
	> service postgresql start
	> to start database service

- launch Armitage tool
- the **Armitage** main window appears.
- Click on **Hosts** from the **Menu** bar and navigate to **Nmap Scan** --> **Intense Scan** to scan for live hosts in the network.
- The **Input** pop-up appears. Type a target IP address.
- After the completion of scan, a **Message** pop-up appears, click **OK**.
- Observe that the target host ( #ip ) appears on the screen.
- Now, from the left-hand pane, expand the **payload** node, and then navigate to **windows** --> **meterpreter**; double-click **meterpreter_reverse_tcp**.
- The **windows/meterpreter_reverse_tcp** window appears. Scroll down to the **LPORT** Option, and change the port **Value** to **444**. In the **Output** field, select **exe** from the drop-down options; click **Launch**.
- The **Save** window appears. Select **Desktop** as the location, set the **File Name** as **malicious_payload.exe**, and click the **Save** button.
- now back to terminal
	> cp /root/Desktop/malicious_payload.exe /var/www/html/share
	> to copy file to shared folder
	> service apache2 start (to start the apache server)
	
	
- Now back to Armitage and double click meterpreter_reverse_tcp
- The **windows/meterpreter_reverse_tcp** window appears. Scroll down to **LPORT** Option and change the port Value to **444**. Ensure that the **multi/handler** option is selected in the **Output** field; click **Launch**.
- Now go to target machine (windows) and enter http://#hostip/share
	- Here, we are sending the malicious payload through a shared directory; however, in real-time, you can send it via an attachment in an email or through physical means such as a hard drive or pen drive.
- run malicious_payload.exe
- Now go back to host linux machine
- Observe that one session has been created or opened in the **Meterpreter** **shell**, as shown in the screenshot, and the host icon displays the target system name (**WINDOWS10**).
- Right-click on the target host and navigate to **Meterpreter 1** --> **Interact** --> **Meterpreter Shell**.
- A new **Meterpreter 1** tab appears. Type **sysinfo** and press **Enter** to view the system details of the exploited system.
- Using this option, you can perform various functions such as uploading a file, making a directory, and listing all drives present in the target system.
- Similarly, you can explore other options such as **Desktop (VNC)**, **Show Processes**, **Log Keystrokes**, and **Webcam Shot**.
- You can also escalate privileges in the target system using the **Escalate Privileges** option and further steal tokens, dump hashes, or perform other activities.