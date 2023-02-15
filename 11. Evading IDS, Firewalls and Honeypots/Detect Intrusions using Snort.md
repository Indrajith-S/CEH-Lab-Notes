- Snort is an open-source network intrusion detection system, capable of performing real-time traffic analysis and packet logging on IP networks. It can perform protocol analysis and content searching/matching and is used to detect a variety of attacks and probes such as buffer overflows, stealth port scans, CGI attacks, SMB probes, and OS fingerprinting attempts. It uses a flexible rules language to describe traffic to collect or pass, as well as a detection engine that utilizes a modular plug-in architecture.
1. Navigate to **Z:\CEHv11 Module 12 Evading IDS, Firewalls, and Honeypots\Intrusion Detection Tools\Snort** and double-click the **Snort_2_9_15_Installer.exe** file to start the Snort installation.
    
    > If an **Open File - Security warning** pop-up window appears, click **Run**.
    
    ![2020-06-30_13-53-50.png](https://labondemand.blob.core.windows.net/content/lab73287/2020-06-30_13-53-50.png)
    
2.  Accept the **License Agreement** and install Snort by selecting the default options that appear **step by step** in the wizard.
    
    ![2020-06-30_13-54-56.png](https://labondemand.blob.core.windows.net/content/lab73287/2020-06-30_13-54-56.png)
    
3.  A window appears after the successful installation of Snort; click **Close**.
    
4.  Click **OK** to exit the **Snort Installation** window.
    
    > Snort requires **WinPcap** to be installed on your machine. In this lab environment, we have already installed WinPcap drivers for packet capturing.
    
    ![2020-06-30_13-55-46.png](https://labondemand.blob.core.windows.net/content/lab73287/2020-06-30_13-55-46.png)
    
5.  By default, Snort installs itself in **C:\Snort** (C:\ or D:\, depending on the disk drive in which the OS is installed).
    
    ![2020-06-30_13-57-16.png](https://labondemand.blob.core.windows.net/content/lab73287/2020-06-30_13-57-16.png)
    
6.  Navigate to the **etc** folder in the specified location, **Z:\CEHv11 Module 12 Evading IDS, Firewalls, and Honeypots\Intrusion Detection Tools\Snort\snortrules-snapshot-29150\etc** of the Snort rules; copy **snort.conf** and paste it in **C:\Snort\etc**.
    
7.  **snort.conf** is already present in **C:\Snort\etc**; replace the file with the newly copied file.
    
    ![2020-06-30_13-59-13.png](https://labondemand.blob.core.windows.net/content/lab73287/2020-06-30_13-59-13.png)
    
8.  Copy the **so_rules** folder from **Z:\CEHv11 Module 12 Evading IDS, Firewalls, and Honeypots\Intrusion Detection Tools\Snort\snortrules-snapshot-29150** and paste into **C:\Snort**.
    
    ![2020-06-30_14-02-30.png](https://labondemand.blob.core.windows.net/content/lab73287/2020-06-30_14-02-30.png)
    
9.  Copy the **preproc_rules** folder from **Z:\CEHv11 Module 12 Evading IDS, Firewalls, and Honeypots\Intrusion Detection Tools\Snort\snortrules-snapshot-29150**, and paste it into **C:\Snort**. The **preproc_rules** folder is already present in **C:\Snort**; replace this folder with the **preproc_rules** folder taken from the specified location.
    
    ![2020-06-30_14-03-34.png](https://labondemand.blob.core.windows.net/content/lab73287/2020-06-30_14-03-34.png)
    
10.  Using the same method, copy the **rules** folder from **Z:\CEHv11 Module 12 Evading IDS, Firewalls, and Honeypots\Intrusion Detection Tools\Snort\snortrules-snapshot-29150** and paste into **C:\Snort**.
    
    ![2020-06-30_14-04-57.png](https://labondemand.blob.core.windows.net/content/lab73287/2020-06-30_14-04-57.png)
    
11.  Now right-click on the **Windows Start** icon and click **Run** from the menu.
    
    ![2020-06-30_14-06-06.png](https://labondemand.blob.core.windows.net/content/lab73287/2020-06-30_14-06-06.png)
    
12.  The **Run** window appears; type **cmd** in the **Open** field and click **OK** to launch command prompt window.
    
    ![2020-06-30_14-10-06.png](https://labondemand.blob.core.windows.net/content/lab73287/2020-06-30_14-10-06.png)
    
13.  The **Command Prompt** window appears; type **cd C:\Snort\bin** and press **Enter** to access the bin folder in the command prompt.
    
    ![ev1.jpg](https://labondemand.blob.core.windows.net/content/lab73287/ev1.jpg)
    
14.  Type **snort** and press **Enter**.
    
    ![ev2.PNG](https://labondemand.blob.core.windows.net/content/lab73287/ev2.PNG)
    
15.  Snort initializes; wait for it to complete. After completion press **Ctrl+C**, Snort exits and comes back to **C:\Snort\bin**.
    
16.  Now type **snort -W**. This command lists your machine’s physical address, IP address, and Ethernet Drivers, but all are disabled by default.
    
    ![ev3.jpg](https://labondemand.blob.core.windows.net/content/lab73287/ev3.jpg)
    
17.  Observe your Ethernet Driver **index number** and write it down (in this lab, it is **1**).
    
18.  To enable the Ethernet Driver, in the command prompt, type **snort -dev -i 1** and press **Enter**.
    
19.  You see a rapid scroll text in the command prompt, which means that the Ethernet Driver is enabled and working properly.
    
    ![ev7.PNG](https://labondemand.blob.core.windows.net/content/lab73287/ev7.PNG)
    
20.  Leave the Snort command prompt window open, and launch another command prompt window.
    
21.  In a new command prompt, type **ping google.com** and press **Enter**.
    
    ![ev4.jpg](https://labondemand.blob.core.windows.net/content/lab73287/ev4.jpg)
    
22.  This ping command triggers a Snort alert in the Snort command prompt with rapid scrolling text.
    
    > The Google IP address will differ in your lab environment.
    
    ![ev6.png](https://labondemand.blob.core.windows.net/content/lab73287/ev6.png)
    
23.  Close both command prompt windows. The verification of Snort installation and the triggering alert is complete, and Snort is working correctly in verbose mode.
    
24.  Configure the **snort.conf** file, located at **C:\Snort\etc**.
    
25.  Open the **snort.conf** file with **Notepad++**.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab73287/screens/wc0stvze.jpg)
    
26.  Scroll down to the **Step #1: Set the network variables** section (Line 41) of the **snort.conf** file. In the **HOME_NET** line (Line 45), replace **any** with the IP addresses of the machine (target machine) on which Snort is running. Here, the target machine is **Windows Server 2019** and the IP address is **10.10.10.19**.
    
    > This IP address may vary in your lab environment.
    
27.  Leave the **EXTERNAL_NET any** line as it is.
    
28.  If you have a **DNS Server**, then make changes in the **DNS_SERVERS** line by replacing **$HOME_NET** with your DNS Server IP address; otherwise, leave this line as it is.
    
    > Here, the DNS server is **8.8.8.8**.
    
    ![ev9.jpg](https://labondemand.blob.core.windows.net/content/lab73287/ev9.jpg)
    
29.  The same applies to SMTP_SERVERS, HTTP_SERVERS, SQL_SERVERS, TELNET_SERVERS, and SSH_SERVERS.
    
30.  Remember that if you do not have any servers running on your machine, leave the line as it is. **DO NOT** make any changes in that line.
    
31.  Scroll down to **RULE_PATH** (Line 104). In Line 104, replace **../rules** with **C:\Snort\rules** in Line 105, replace **../so_rules** with **C:\Snort\so_rules** and in Line 106, replace **../preproc_rules** with **C:\Snort\preproc_rules**.
    
    ![ev10.jpg](https://labondemand.blob.core.windows.net/content/lab73287/ev10.jpg)
    
32.  In Lines 109 and 110, replace **../rules** with **C:\Snort\rules**. Minimize the **Notepad++** window.
    
    ![ev11.jpg](https://labondemand.blob.core.windows.net/content/lab73287/ev11.jpg)
    
33.  Navigate to **C:\Snort\rules**, and create two text files; name them **white_list** and **black_list** and change their file extensions from **.txt** to **.rules**.
    
    > To create a text file, right-click anywhere inside the rules window and navigate to **New --> Text Document**.
    
34.  While changing the extension, if any pop-up appears, click **Yes**.
    
35.  Switch back to **Notepad++**, scroll down to the **Step #4: Configure dynamic loaded libraries** section (Line 238). **Configure dynamic loaded libraries** in this section.
    
36.  Add the path to dynamic preprocessor libraries (Line 243); replace **/usr/local/lib/snort_dynamicpreprocessor/** with your dynamic preprocessor libraries folder location.
    
37.  In this lab, the dynamic preprocessor libraries are located at **C:\Snort\lib\snort_dynamicpreprocessor**.
    
38.  At the path to base preprocessor (or dynamic) engine (Line 246), replace **/usr/local/lib/snort_dynamicengine/libsf_engine.so** with your base preprocessor engine **C:\Snort\lib\snort_dynamicengine\sf_engine.dll**.
    
39.  Ensure that the dynamic rules libraries (Line 250) is commented out, as you have already configured the libraries in dynamic preprocessor libraries.
    
    > Add (**space**) in between **#** and dynamicdetection (Line 250).
    
    ![ev12.jpg](https://labondemand.blob.core.windows.net/content/lab73287/ev12.jpg)
    
40.  Scroll down to the **Step #5: Configure preprocessors** section (Line 253), the listed preprocessor. This does nothing in IDS mode, however, it generates errors at runtime.
    
41.  Comment out all the preprocessors listed in this section by adding ‘**#**’ and (**space**) before each preprocessor rule (262-266).
    
    > To ‘comment out’ is to render a block of code inert by turning it into a comment.
    
    ![ev13.jpg](https://labondemand.blob.core.windows.net/content/lab73287/ev13.jpg)
    
42.  Scroll down to line 326 and delete **lzma** keyword and a (**space**).
    
    ![ev15.jpg](https://labondemand.blob.core.windows.net/content/lab73287/ev15.jpg)
    
43.  Scroll down to **Step #6: Configure output plugins** (Line 513). In this step, provide the location of the **classification.config** and **reference.config** files.
    
44.  These two files are in **C:\Snort\etc**. Provide this location of files in the configure output plugins (in Lines 532 and 533) (i.e., **C:\Snort\etc\classification.config** and **C:\Snort\etc\reference.config**).
    
    ![ev16.jpg](https://labondemand.blob.core.windows.net/content/lab73287/ev16.jpg)
    
45.  In **Step #6**, add to line (534) **output alert_fast: alerts.ids:** this command orders Snort to dump all logs into the **alerts.ids** file.
    
    ![00.jpg](https://labondemand.blob.core.windows.net/content/lab73287/00.jpg)
    
46.  In the **snort.conf** file, find and replace the **ipvar** string with **var**. To do this, press **Ctrl+H** on the keyboard. The **Replace** window appears; enter **ipvar** in the **Find what** : text field, enter **var** in the **Replace with** : text field, and click **Replace All**.
    
    > You will get a notification saying 11 occurrences were replaced.
    
47.  By default, the string is **ipvar**, which is not recognized by Snort: replace with the **var** string, and then **close** the window.
    
    > Snort now supports multiple conﬁgurations based on VLAN Id or IP subnet within a single instance of Snort. This allows administrators to specify multiple snort conﬁguration ﬁles and bind each conﬁguration to one or more VLANs or subnets rather than running one Snort for each conﬁguration required.
    
    ![ev19.jpg](https://labondemand.blob.core.windows.net/content/lab73287/ev19.jpg)
    
48.  Click **Close** to close the **Replace** window.
    
49.  Save the **snort.conf** file by pressing **Ctrl+S** and close Notepad++ window.
    
50.  Before running Snort, you need to enable detection rules in the Snort rules file. For this task, we have enabled the ICMP rule so that Snort can detect any host discovery ping probes directed at the system running Snort.
    
51.  Navigate to **C:\Snort\rules** and open the **icmp-info.rules** file with **Notepad++**.
    
52.  In line 21, type **alert icmp $EXTERNAL_NET any -> $HOME_NET 10.10.10.19 (msg:"ICMP-INFO PING"; icode:0; itype:8; reference:arachnids,135; reference:cve,1999-0265; classtype:bad-unknown; sid:472; rev:7;)** and save. Close the **Notepad++** window.
    
    > The IP address (10.10.10.19) mentioned in $HOME_NET may vary in your lab environment.
    
    ![ev20.jpg](https://labondemand.blob.core.windows.net/content/lab73287/ev20.jpg)
    
53.  Now right-click on the **Windows Start** icon and click **Run** from the menu.
    
54.  In the **Run** window, type **cmd** in the **Open** field and press **Enter**: This will launch a command prompt window.
    
55.  In the command prompt window, type **cd C:\Snort\bin** and press **Enter**.
    
56.  Type **snort -iX -A console -c C:\Snort\etc\snort.conf -l C:\Snort\log -K ascii** and press **Enter** to start Snort (replace **X** with your device index number; in this lab: **X** is 1).
    
    ![ev23.jpg](https://labondemand.blob.core.windows.net/content/lab73287/ev23.jpg)
    
57.  If you receive a **fatal error**, you should first **verify** that you have typed all modifications correctly into the **snort.conf** file, and then search through the file for **entries** matching your fatal error message.
    
58.  If you receive an error stating “**Could not create the registry key**,” then run the command prompt as **Administrator**.
    
59.  Snort starts running in IDS mode. It first initializes output plug-ins, preprocessors, plug-ins, loads dynamic preprocessors libraries, rule chains of Snort, and then logs all signatures.
    
60.  If you have entered all command information correctly, you receive a comment stating **Commencing packet processing (pid=xxxx)** (the value of xxxx may be any number; in this lab, it is 5384), as shown in the screenshot.
    
    ![ev24.jpg](https://labondemand.blob.core.windows.net/content/lab73287/ev24.jpg)
    
61.  After initializing interface and logged signatures, Snort starts and waits for an attack and triggers alerts when attacks occur on the machine.
    
62.  Leave the Snort command prompt running.
    
63.  Attack your own machine, and check whether Snort detects it or not.
    
64.  Now, click on [Windows 10](https://labclient.labondemand.com/Instructions/05ceaed6-2521-4bdb-be27-4d8726fd747a?rc=10#) to switch to the **Windows 10** machine (**Attacker Machine**). Click [Ctrl+Alt+Delete](https://labclient.labondemand.com/Instructions/05ceaed6-2521-4bdb-be27-4d8726fd747a?rc=10#) to activate the machine.
    
    > Alternatively, you can also click **Ctrl+Alt+Delete** button under **Windows 10** machine thumbnail in the **Resources** pane or Click **Ctrl+Alt+Delete** button under Commands (**thunder** icon) menu.
    
65.  By default, **Admin** user profile is selected, click Pa$$w0rd to paste the password in the Password field and press **Enter** to login.
    
    > Alternatively, you can also click **Pa$$w0rd** under **Windows 10** machine thumbnail in the **Resources** pane or Click **Type Text | Type Password** button under Commands (**thunder** icon) menu.
    
    > Networks screen appears, click **Yes** to allow your PC to be discoverable by other PCs and devices on the network.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab73287/screens/5geweews.jpg)
    
66.  Open the command prompt and issue the command **ping 10.10.10.19 -t** from the **Attacker Machine**
    
    > **10.10.10.19** is the IP address of the Windows Server 2019. This IP address may differ in your lab environment.
    
    ![ev25.jpg](https://labondemand.blob.core.windows.net/content/lab73287/ev25.jpg)
    
67.  Click [Windows Server 2019](https://labclient.labondemand.com/Instructions/05ceaed6-2521-4bdb-be27-4d8726fd747a?rc=10#) to return to the **Windows Server 2019** machine. Observe that Snort triggers an alarm, as shown in the screenshot:
    
    ![ev26.jpg](https://labondemand.blob.core.windows.net/content/lab73287/ev26.jpg)
    
68.  Press **Ctrl+C** to **stop** Snort; snort exits.
    
    ![ev27.jpg](https://labondemand.blob.core.windows.net/content/lab73287/ev27.jpg)
    
69.  Go to the **C:\Snort\log\10.10.10.10** folder and open the **ICMP_ECHO.ids** file with **Notepad++**. You see that all the log entries are saved in the **ICMP_ECHO.ids** file.
    
    > The folder name **10.10.10.10** might vary in your lab environment, depending on the IP address of the **Windows 10** machine.
    
    ![ev28.jpg](https://labondemand.blob.core.windows.net/content/lab73287/ev28.jpg)
    
    > This means that whenever an attacker attempts to connect or communicate with the machine, Snort immediately triggers an alarm
    
    > This will make you aware of the intrusion and can thus take certain security measures to disconnect the lines of communication with the attacker’s machine.