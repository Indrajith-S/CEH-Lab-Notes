- The Social-Engineer Toolkit (SET) is an open-source, Python-driven tool that enables penetration testing via social engineering. It is a generic exploit that can be used to carry out advanced attacks against human targets in order to get them to offer up sensitive information. SET categorizes attacks according to the attack vector used to trick people such as email, web, or USB. The toolkit attacks human weakness, exploiting people’s trust, fear, avarice, or helping natures.
- In this task, we will sniff user credentials on the Android platform using SET.
- Open Terninal
	> sudo su
	> cd 
	> cd setoolkit
	> ./setoolkit (to launch Social-Engineer Toolkit)
	
	> 1 (to choose Social-Engineering Attacks)
	> 2 (to choose Website Attack Vectors)
	> 3 (to choose Credential Harvester Attack method)
	> 2 (to choose site cloner)
	
	> Enter #hostip 
	> Enter #url 
	
- The cloning of the website completes, a highlighted message appears
- Having successfully cloned a website, you must now send the IP address of your machine to a victim and try to trick him/her into clicking on the link.
- After logging into your email account, click the **Compose** button in the left pane and compose a fake but enticing email to lure a user into opening the email and clicking on a malicious link.
	- A good way to conceal a malicious link in a message is to insert text that looks like a legitimate online ticket booking account URL (in this case), but that actually links to your malicious cloned certifiedhacker page.
- click insert link icon.
- In the **Edit Link** window, first type the actual address of your cloned site in the **Web address** field under the **Link to** section. Then, type the fake URL in the **Text to display** field.
- The fake URL should appear in the message body.
- Verify that the fake URL is linked to the correct cloned site: in Gmail, click the link; the actual URL will be displayed in a “**Go to link**” pop-up. Once verified, send the email to the intended user.



- Open Android machine (as victim)
- In the **Google Chrome** browser window, sign in to the email account to which you sent the phishing mail as an attacker. Open the email you sent previously and click to open the malicious link.
- When the victim (you in this case) clicks the URL, a new tab opens up, and he/she will be presented with a replica of cloned site.
- The hotel booking page appears, scroll-down to the end of the page. Here, the victim will be prompted to enter his/her username and password into the form fields, which appear as they do on the genuine website. When the victim enters the **Username** and **Password** and clicks **Login**, the page shows an error.


- In the host machine, in the terminal window, scroll down to find an **Username** and **Password**, displayed in plain text.
