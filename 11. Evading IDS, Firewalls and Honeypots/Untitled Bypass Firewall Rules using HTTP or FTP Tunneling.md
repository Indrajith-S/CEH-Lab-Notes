- HTTP tunneling technology allows attackers to perform various Internet tasks despite the restrictions imposed by firewalls. This method can be implemented if the target company has a public web server with port 80 used for HTTP traffic that is unfiltered by its firewall. This technology encapsulates data inside HTTP traffic (port 80). Many firewalls do not examine the payload of an HTTP packet to confirm that it is legitimate, thus it is possible to tunnel traffic via TCP port 80.

- HTTPort allows users to bypass the HTTP proxy, which blocks Internet access to e-mail, instant messengers, P2P file sharing, ICQ, News, FTP, IRC, etc. Here, the Internet software is configured, so that it connects to a local PC as if it is the required remote server; HTTPort then intercepts that connection and runs it via a tunnel through the proxy. HTTPort can work on devices such as proxies or firewalls that allow HTTP traffic. Thus, HTTPort provides access to websites and Internet apps. HTTPort performs tunneling using one of two modes: SSL/CONNECT mode and a remote host.

- The remote host method is capable of tunneling through any proxy. HTTPort uses a special server software called HTTHost, which is installed outside the proxy-blocked network. It is a web server, and thus when HTTPort is tunneling, it sends a series of HTTP requests to the HTTHost. The proxy responds as if the user is surfing a website and thus allows the user to do so. HTTHost, in turn, performs its half of the tunneling and communicates with the target servers. This mode is much slower, but works in the majority of cases and features strong data encryption that makes proxy logging useless.

- Here, we will learn how networks can be scanned, and how to use HTTPort and HTTHost to bypass firewall restrictions and access files.



1.  Now, you must ensure that **IIS Admin Service** and **World Wide Web Publishing services** are not running
    
2.  Click **Start** and click the **Windows Administrative Tools** app. The **Windows Administrative Tools** window appears; double-click **Services** to launch.
    
    ![ev125.jpg](https://labondemand.blob.core.windows.net/content/lab73287/ev125.jpg)
    
3.  In the **Services** window, scroll down to **World Wide Web Publishing Service** and you can observe that the service is **Disabled** under the **Startup Type** column, as shown in the screenshot.
    
    ![ev126.jpg](https://labondemand.blob.core.windows.net/content/lab73287/ev126.jpg)
    
4.  Similarly, check **IIS Admin Service**; stop the program if it is running.
    
5.  Navigate to **Z:\CEHv11 Module 12 Evading IDS, Firewalls, and Honeypots\HTTP Tunneling Tools\HTTHost** and double-click **htthost.exe**.
    
    ![2020-06-30_14-40-24.png](https://labondemand.blob.core.windows.net/content/lab73287/2020-06-30_14-40-24.png)
    
6.  If the **Open File - Security Warning** pop-up appears, click **Run**.
    
7.  A **HTTHost** wizard appears; click the **Options** tab.
    
8.  On the **Options** tab, leave **90** as the port number in the **Port** field under the **Network** section. Keep the other settings on default, except for **Personal password**, which should contain any other password. In this task, the **Personal password** is **“magic**.”
    
    > Typically, HTTP tunneling should be performed using port 80. Port 80 is being used to host the local websites, therefore we have used port 90 for this lab.
    
9.  Ensure that **Revalidate DNS names** and **Log connections** are checked and click **Apply**.
    
    ![im10.png](https://labondemand.blob.core.windows.net/content/lab73287/im10.png)
    
10.  Navigate to the **Application log** tab and check if the last line is **Listener: listening at 0.0.0.0:90**, which ensures that HTTHost is running properly and has begun to listen on **port 90**.
    
    ![ev128.png](https://labondemand.blob.core.windows.net/content/lab73287/ev128.png)
    
11.  Now, leave **HTTHost** running, and do not turn off the **Windows Server 2016** machine.
    
12.  Now, click [Windows Server 2019](https://labclient.labondemand.com/Instructions/05ceaed6-2521-4bdb-be27-4d8726fd747a?rc=10#) to switch to the **Windows Server 2019** machine and launch **Control Panel**, as shown in the screenshot.
    
    ![ev129.jpg](https://labondemand.blob.core.windows.net/content/lab73287/ev129.jpg)
    
13.  The **Control Panel** window appears with all control panel items displayed. Select **Windows Defender Firewall**.
    
    ![ev130.jpg](https://labondemand.blob.core.windows.net/content/lab73287/ev130.jpg)
    
14.  The **Windows Defender Firewall** control panel appears; click the **Turn Windows Defender Firewall on or off** link in the left pane.
    
    ![ev131.jpg](https://labondemand.blob.core.windows.net/content/lab73287/ev131.jpg)
    
15.  The **Customize Settings** window appears.
    
16.  Select **Turn on Windows Defender Firewall** under **Private network settings** and **Public network settings**.
    
17.  Click **OK**.
    
    ![ev132.jpg](https://labondemand.blob.core.windows.net/content/lab73287/ev132.jpg)
    
18.  The firewall is successfully turned on. Now, click **Advanced settings** in the left pane.
    
    ![ev133.jpg](https://labondemand.blob.core.windows.net/content/lab73287/ev133.jpg)
    
19.  The **Windows Firewall with Advanced Security** window appears.
    
20.  Select **Outbound Rules** in the left pane. A list of outbound rules is displayed. Click **New Rule…** in the right pane under **Outbound Rules**.
    
    ![ev134.jpg](https://labondemand.blob.core.windows.net/content/lab73287/ev134.jpg)
    
21.  In **New Outbound Rule Wizard**, select **Port** as **Rule Type** and click **Next**.
    
    ![ev135.png](https://labondemand.blob.core.windows.net/content/lab73287/ev135.png)
    
22.  Select **All remote ports** in **Protocol and Ports** and click **Next**.
    
    ![ev136.png](https://labondemand.blob.core.windows.net/content/lab73287/ev136.png)
    
23.  In **Action, Block the connection** is selected by default and click **Next**.
    
    ![ev137.png](https://labondemand.blob.core.windows.net/content/lab73287/ev137.png)
    
24.  In the **Profile** section, ensure that all options (**Domain**, **Private**, and **Public**) are checked and click **Next**.
    
    ![ev138.png](https://labondemand.blob.core.windows.net/content/lab73287/ev138.png)
    
25.  In **Name**, type **Port 21 Blocked** in the **Name** field and click **Finish**.
    
    ![ev139.png](https://labondemand.blob.core.windows.net/content/lab73287/ev139.png)
    
26.  The new rule **Port 21 Blocked** is created, as shown in the screenshot.
    
    ![ev140.png](https://labondemand.blob.core.windows.net/content/lab73287/ev140.png)
    
27.  Right-click the newly created rule (**Port 21 Blocked**) and click **Properties**.
    
    ![ev141.jpg](https://labondemand.blob.core.windows.net/content/lab73287/ev141.jpg)
    
28.  The **Properties** window for **Port 21 Blocked** rule appears.
    
29.  Select the **Protocols and Ports** tab. In the **Remote port:** field, select the **Specific Ports** option from the drop-down list and enter the port number as **21**.
    
30.  Leave the other default settings, click **Apply**, and then click **OK**.
    
31.  Disable the rule and confirm that you can connect to the ftp site.
    
32.  Right-click the newly added rule and click **Disable Rule**.
    
    ![ev143.jpg](https://labondemand.blob.core.windows.net/content/lab73287/ev143.jpg)
    
33.  Launch the command prompt and issue **ftp 10.10.10.10**. You will be asked to enter the username.
    
    ![ev144.png](https://labondemand.blob.core.windows.net/content/lab73287/ev144.png)
    
    > In the above-mentioned command, **10.10.10.10** refers to the IP address of **Windows 10** where the ftp site is located. Make sure that you issue the IP address of Windows 10 in your lab environment.
    
34.  This means you can establish an FTP connection, and then close the command prompt window.
    
35.  Now, enable the rule and check whether you can establish a connection.
    
36.  Right-click the newly added rule and click **Enable Rule**.
    
37.  Launch **Command Prompt** and check whether you can connect to the ftp site by issuing the command **ftp 10.10.10.10**.
    
38.  The added outbound rule should block the connection, as shown in the screenshot.
    
    ![ev145.png](https://labondemand.blob.core.windows.net/content/lab73287/ev145.png)
    
    > In the above-mentioned command, **10.10.10.10** refers to the IP address of **Windows 10**, where the ftp site is located. Make sure that you issue the IP address of Windows 10 in your lab environment.
    
39.  Now, we will perform **tunneling** using **HTTPort** to establish a connection with the FTP site located on **Windows 10**.
    
40.  Navigate to **Z:\CEHv11 Module 12 Evading IDS, Firewalls, and Honeypots\HTTP Tunneling Tools\HTTPort** and double-click **httport3snfm.exe**.
    
    ![2020-06-30_14-41-51.png](https://labondemand.blob.core.windows.net/content/lab73287/2020-06-30_14-41-51.png)
    
41.  If a **User Account Control** pop-up appears, click **Yes**.
    
42.  Follow the installation steps to install HTTPort.
    
    ![ev146.png](https://labondemand.blob.core.windows.net/content/lab73287/ev146.png)
    
43.  Launch HTTPort (**Httport3SNFM**) from the **Start** menu.
    
    ![ev147.jpg](https://labondemand.blob.core.windows.net/content/lab73287/ev147.jpg)
    
44.  An **Introduction to HTTPort** wizard appears; click **Next** five times, until you come to the last wizard pane, and then click **Close**.
    
    ![ev148.png](https://labondemand.blob.core.windows.net/content/lab73287/ev148.png)
    
45.  The **HTTPort** main window (**HTTPort 3.SNFM**) appears, as shown in the screenshot.
    
46.  On the **Proxy** tab, enter the **Host name** or **IP address** (**10.10.10.16**) of the machine where HTTHost is running (**Windows Server 2016**).
    
    > The IP address of **Windows Server 2016** may vary in your lab environment.
    
47.  Enter the **Port** number **90**.
    
48.  In the **Misc. options** section, select **Remote host** from the **Bypass mode** drop-down list.
    
49.  In the **Use personal remote host at (blank = use public)** section, re-enter the IP address of **Windows Server 2016 (10.10.10.16)** and port number **90**.
    
50.  Enter the password **magic** into the **Password** field.
    
    ![ev149.png](https://labondemand.blob.core.windows.net/content/lab73287/ev149.png)
    
51.  Select the **Port mapping** tab, and click **Add** to create a new mapping.
    
    ![ev150.png](https://labondemand.blob.core.windows.net/content/lab73287/ev150.png)
    
52.  Right-click the **New mapping** node, and click **Edit**.
    
    ![ev151.jpg](https://labondemand.blob.core.windows.net/content/lab73287/ev151.jpg)
    
53.  Rename this as **ftp test** (you can enter the name of your choice).
    
54.  Right-click the node below **Local port**; then click **Edit** and enter the port value as **21**.
    
55.  Right-click the node below **Remote host**; click **Edit** and rename it as **10.10.10.10**.
    
56.  Right-click the node below **Remote port**; then click **Edit** and enter the port value as **21**.
    
    > **10.10.10.10** specifies in Remote host node is the IP address of the **Windows 10** machine that is hosting the FTP site.
    
    ![ev152.png](https://labondemand.blob.core.windows.net/content/lab73287/ev152.png)
    
57.  Switch to the **Proxy** tab and click **Start** to begin the HTTP tunneling.
    
    > If you get an error, ignore it.
    
    ![ev153.png](https://labondemand.blob.core.windows.net/content/lab73287/ev153.png)
    
58.  HTTPort intercepts the ftp request to the localhost and tunnels through it. HTTHost is installed in the remote machine to connect you to **10.10.10.10**.
    
    > This means you may not access the ftp site directly by issuing **ftp 10.10.10.10** in the command prompt, but you will be able to access it through the localhost by issuing the command **ftp 127.0.0.1**.
    
59.  In **Windows Server 2019**; launch **Command Prompt**, type **ftp 10.10.10.10**, and press **Enter**. The ftp connection will be blocked by the outbound firewall rule.
    
    ![ev154.png](https://labondemand.blob.core.windows.net/content/lab73287/ev154.png)
    
60.  Now, launch a new **Command Prompt**, type **ftp 127.0.0.1**, and press **Enter**. You should be able to connect to the site.
    
    > If you issue this command without starting HTTPort, the connection to the FTP site fails, stating that the FTP connection is refused.
    
    ![ev155.png](https://labondemand.blob.core.windows.net/content/lab73287/ev155.png)
    
61.  Enter the credentials of any user account on **Windows 10**. In this lab, we are using the credentials of the **Jason** account (username: **Jason**; Password: **qwerty**). Type the username and press **Enter**.
    
    > The password you enter will not be visible.
    
    ![ev156.png](https://labondemand.blob.core.windows.net/content/lab73287/ev156.png)
    
62.  You are successfully logged in, even after adding a firewall outbound rule inferring that a tunnel has been established by HTTPort and HTTHost and therefore have bypassed the firewall.
    
63.  Now you have the access and ability to add files in the ftp directory located in the **Windows 10** machine.
    
64.  Type **mkdir Test** and press **Enter**.
    
    ![ev157.png](https://labondemand.blob.core.windows.net/content/lab73287/ev157.png)
    
65.  Now, Click [Windows 10](https://labclient.labondemand.com/Instructions/05ceaed6-2521-4bdb-be27-4d8726fd747a?rc=10#) to switch to the **Windows 10** machine.
    
66.  A directory named **Test** will be created in the **FTP** folder on the **Windows 10** (location: **C:\FTP**) machine, as shown in the screenshot:
    
    ![ev158.png](https://labondemand.blob.core.windows.net/content/lab73287/ev158.png)
    
67.  Thus, you are able to bypass HTTP proxies as well as firewalls, and thereby access files beyond them.