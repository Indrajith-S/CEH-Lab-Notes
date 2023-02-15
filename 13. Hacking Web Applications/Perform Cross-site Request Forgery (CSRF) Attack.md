- CSRF, also known as a one-click attack, occurs when a hacker instructs a user’s web browser to send a request to the vulnerable website through a malicious web page. Financial websites commonly contain CSRF vulnerabilities. Usually, outside attackers cannot access corporate intranets, so CSRF is one of the methods used to enter these networks. The inability of web applications to differentiate a request made using malicious code from a genuine request exposes it to the CSRF attack. These attacks exploit web page vulnerabilities that allow an attacker to force an unsuspecting user’s browser to send malicious requests that they did not intend.

- CSRF attacks can be performed using various techniques and tools. Here, we will perform a CSRF attack using WPScan.

- Now, open any web browser (here, **Mozilla Firefox**). In the address bar place your mouse cursor, click http://10.10.10.16:8080/CEH/wp-login.php? and press **Enter**.
- A **WordPress** webpage appears. Type **Username or Email Address** and **Password** as **admin** and **qwerty@123**. Click the **Log In** button.
- Assume that you have installed and configured the **Firewall plugin** for this site and that you want to check the security configurations.
- Hover your mouse cursor on **Plugins** in the left pane and click **Installed Plugins**.
- In the **Plugins** page, observe that **leenk.me** is installed. Click **Activate** under the **leenk.me** plugin to activate the plugin.
- Refresh the page and you will observe that the **leenk.me** plugin option appears in the left pane; click it.
- The **leenk.me General Settings** page appears. Tick the **Facebook** checkbox in the **Choose which social network modules you want to enable for this site** option under the **Administrator Options** section and click the **Save Settings** button.
- The **leenk.me General Settings** page appears, as shown in the screenshot. Ensure that under the **Administrator Options** section, the **Facebook** checkbox is selected in the **Choose which social network modules you want to enable for this site** option and click the **Facebook Settings** hyperlink.
- A **Facebook Settings** page appears; under **Message Settings**, enter the details below:
    -   **Default Message**: This is CEH lab.
    -   **Default Link Name**: CEH.com
    -   **Default Caption**: CEH Labs
- Clear the **Default Description** text field. Leave the other settings to default and click the **Save Settings** button to save the settings.
- Click [Parrot Security](https://labclient.labondemand.com/Instructions/9baf6657-1025-452d-b133-7e88ffcb9dd2?rc=10#) to switch to the **Parrot Security** machine.
- Click the Applications icon from the top section of Desktop and navigate to Internet --> Google Chrome browser.
- The **Google Chrome** window appears. Type **https://wpscan.com/login** into the address bar and press **Enter**.
- The **Edit Profile** page appears; in the **API Token** section and observe the API Token. Note down or copy this API Token; we will use this token in the later steps.
- Open Terminal
	> sudo su
	> cd
	> wpscan --api-token #apitoken --url http:// #targetip:8080/ #domain --plugins-detection aggressive --enumerate vp
	- **--enumerate vp**: specifies the enumeration of vulnerable plugins.
	- The result appears, displaying detailed information regarding the target website.
	- Scroll down to the **Plugin(s) Identified** section, and observe the installed vulnerable plugins (**akismet** and **leenkme**) on the target website.


- In this task, we will exploit the **CSRF** vulnerability present in the **leenkme** plugin.
- The **Desktop** window appears, copy **Security_Script.html** file.
- Click the **Places** menu at the top of **Desktop** and click **Network** from the drop-down options.
- The **Network** window appears; press the **Ctrl+L** keys. A Location field appears; type **smb://10.10.10.10** and press **Enter** to access the **Windows 10** shared folders.
- A security pop-up appears; enter the **Windows 10** machine credentials (Username: **Admin** and Password: **Pa$$w0rd) and click Connect
- The **Windows shares on 10.10.10.10** window appears; double-click the **CEH-Tools** folder.
- Navigate to **CEHv11 Module 14 Hacking Web Applications** and paste **Security_Script.html** script.
- Navigate to **CEHv11 Module 14 Hacking Web Applications** and paste **Security_Script.html** script in windows server 2016 machine.
- The **Security_Script.html** file opens up in the **Mozilla Firefox** browser, along with a pop-up; click **OK** to continue.
- You will be redirected to the **Facebook Settings** page of the **leenk.me** plugin page. Observe that the field values have been changed, indicating a successful CSRF attack on the website.