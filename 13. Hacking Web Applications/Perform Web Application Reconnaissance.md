- In web application reconnaissance, you must perform various tasks such as server discovery, service discovery, server identification or banner grabbing, and hidden content discovery. A professional ethical hacker or pen tester must gather as much information as possible about the target website by performing web application footprinting using various techniques and tools.

- In this task, we will perform web application reconnaissance to gather information about server IP address, DNS names, location and type of server, open ports and services, make, model, version of the web server software, and server-side technology.
- Perform a Whois lookup to gather information about the IP address of the web server and the complete information about the domain such as its registration details, name servers, IP address, and location.
- Use tools such as **Netcraft** (https://www.netcraft.com), **SmartWhois** (https://www.tamos.com), **WHOIS Lookup** (http://whois.domaintools.com), and Batch **IP Converter** (http://www.sabsoft.com) to perform the Whois lookup.
- Perform DNS Interrogation to gather information about the DNS servers, DNS records, and types of servers used by the target organization. DNS zone data include DNS domain names, computer names, IP addresses, domain mail servers, service records, etc.
- Use tools such as Professional **Toolset** (https://tools.dnsstuff.com), **DNSRecon** (https://github.com), and **DNS Records** (https://network-tools.com), **Domain Dossier** (https://centralops.net) to perform DNS interrogation.


- Open Terminal
	> nmap -T4 -A -v #targetWebsite (to perform port and service discovery scan)
	- In this command, **-T4**: specifies setting time template (0-5), **-A**: specifies aggressive scan, and **-v**: enables the verbose output (include all hosts and ports in the output).

	- Now, perform banner grabbing to identify the make, model, and version of the target web server software.
	    > telnet #targetWebsite 80
	    - The **Trying #targetip …** message appears; type **GET / HTTP/1.0** and press **Enter** two times.
	    - The result appears, displaying information related to the server name and its version, technology used.


### Perform Web Application Reconnaissance using WhatWeb

- WhatWeb identifies websites and recognizes web technologies, including content management systems (CMS), blogging platforms, statistics and analytics packages, JavaScript libraries, web servers, and embedded devices. It also identifies version numbers, email addresses, account IDs, web framework modules, SQL errors, and more.
- Open Terminal
	> whatweb #targetWebsite (to perform website footprinting on the target website)
	> whatweb -v #targetWebsite (to run a verbosity scan on the target website)

	- The result appears, displaying a detailed report on the target website such as its IP address, plugin information, and HTTP header information

	> whatweb --log-verbose=website_report #targetWebsite (to export the results returned by WhatWeb as a text file)
	- In real-time, attackers use this information to determine the website infrastructure and find underlying vulnerabilities, and later exploit them to launch further attacks.


### Perform Web Spidering using OWASP ZAP

- OWASP Zed Attack Proxy (ZAP) is an integrated penetration testing tool for finding vulnerabilities in web applications. It offers automated scanners as well as a set of tools that allow you to find security vulnerabilities manually. ZAP provides functionality for a range of skill levels—from developers to testers new to security testing, to security testing specialists.
- Open Terminal
	> zaproxy (to launch OWASP ZAP
- The **OWASP ZAP** main window appears. Under the **Quick Start** tab, click the **Automated Scan** option under **Welcome to OWASP ZAP**.
- The **Automated Scan** wizard appears; enter the target website under the **URL to attack** field. Leave the other settings to default and click the **Attack** button.
- After performing web spidering, **OWASP ZAP** performs active scanning. Navigate to the **Active Scan** tab to observe the various scanned links.
- After completing the active scan, the results appear under the **Alerts** tab, displaying the various vulnerabilities and issues associated with the target website.
- Now, click on the **Spider** tab from the lower section of the window to view the web spidering information. By default, the **URLs** tab appears under the **Spider** tab.
- The **URLs** tab contains various links for hidden content and functionality associated with the target website.
- Now, navigate to the **Messages** tab under the **Spider** tab to view more detailed information regarding the URLs obtained while performing the web spidering, as shown in the screenshot.
- In real-time, attackers perform web spidering or crawling to discover hidden content and functionality, which is not reachable from the main visible content, to exploit user privileges within the application. It also allows attackers to recover backup copies of live files, configuration and log files containing sensitive data, backup archives containing snapshots of files within the web root, and new functionality that is not linked to the main application.


### Detect Load Balancers using Various Tools

- Organizations use load balancers to distribute web server load over multiple servers and increase the productivity and reliability of web applications. Generally, there are two types of load balancers, namely, DNS load balancers (Layer 4 load balancers) and http load balancers (layer 7 load balancers). You can use various tools such as dig and load balancing detector (lbd) to detect the load balancers of the target organization along with their real IP addresses.
- Here, we will detect load balancers using dig command and lbd tool.

- Open Terminal
	>  dig #targetWebsite 
	- The result appears, displaying the available load balancers of the target website. Here, a single host resolves to multiple IP addresses, which possibly indicates that the host is using a load balancer.
	- dig command provides detailed results and is used to identify whether the target domain is resolving to multiple IP addresses.



	> lbd #targetWebsite (The result appears, displaying the available DNS load balancers used by the target website)
	- lbd (load balancing detector) detects if a given domain uses DNS and http load balancing via the Server: and Date: headers and the differences between server answers. It analyzes the data received from application responses to detect load balancers.


### Identify Web Server Directories

- Web servers host the web applications, so misconfigurations while hosting these web applications may lead to the exposure of critical files and directories over the Internet. A professional ethical hacker or pen tester must identify the target web application’s files and directories exposed on the Internet using various automated tools such as Nmap and Gobuster. This information further helps to gather sensitive information stored in the files and folders.

- Here, we will use Nmap and Gobuster tool to identify web server directories on the target website.


- Open Terminal (using NMAP)
	> nmap -sV --script=http-enum #targetWebsite 
	
	- The result appears, displaying open ports and services, along with their version.
	- Scroll-down in the result and observe the identified web server directories under the **http-enum** section, as shown in the screenshot.
		- In real-time, attackers use various techniques to detect the vulnerabilities in the target web applications hosted by the web servers either to gain administrator-level access to the server or to retrieve sensitive information stored on the server. Attackers use the Nmap NSE script http-enum to enumerate the applications, directories, and files of the web servers that are exposed on the Internet. Through this method, attackers identify critical security vulnerabilities on the target web application.


- Open Terminal (using gobuster)
	> gobuster dir -u #targetWebsite -w common.txt
	
	- **dir**: uses directory or file brute-forcing mode, **-u**: specifies the target URL, and **-w**: is the wordlist file used for directory brute-forcing (here, **common.txt**).
	- In real-time, attackers use Gobuster to scan the target website for web server directories and perform fast-paced enumeration of the hidden files and directories of the target web application. Gobuster is a command-oriented tool used to brute-force URIs in websites, DNS subdomains, and names of the virtual hosts on the target server.


### Perform Web Application Vulnerability Scanning using Vega

- Vega is a web application scanner used to test the security of web applications. It helps you to find and validate SQL Injection, XSS, inadvertently disclosed sensitive information, and other vulnerabilities.
- Launch Vega tool
- The **Subgraph Vega** main window appears.
- Click **Scan** from the menu bar and select **Start New Scan** from the available options.
- The **Select a Scan Target** window appears on the screen. Ensure that the **Enter a base URI for scan** radio button is selected under the **Scan Target** section.
- In the **Enter a base URI for scan** field, enter the target URL (here **http://10.10.10.16:8080/dvwa**) and click **Next**.
	- **10.10.10.16** is the IP address of **Windows Server 2016**, where the **DVWA** site is hosted on port **8080**.
- The **Select Modules** wizard appears; double-click on both of the checkboxes (**Injection Modules** and **Response Processing Modules**) to select all options.
- By checking these options, all modules under these options will be selected. Click **Next**.
- In the **Authentication Options** wizard, leave the settings to default and click **Next**.
- In **Parameters** wizard, leave the settings to default and click **Finish** to initiate the scan.
- The Vega application starts scanning the target website for vulnerabilities. Observe the **Scanner Progress** bar and wait for it to finish.
	- In the left-hand pane, under the **Scan Alerts** section, you can see the scan status as **Auditing**. As soon as Vega completes, the scan status changes to **Completed**.
- After the scanner finishes performing its vulnerability assessment on the target website, it lists the discovered vulnerabilities under **Scan Alert Summary**.
- In the left-pane under **Scan Alerts**, expand the nodes to view the complete vulnerability scan result. Now, choose any one of the discovered vulnerabilities to display it on the respective page, as in the dashboard section.
- Similarly, you can select any vulnerability from the list of discovered vulnerabilities to view its detailed information and then apply appropriate fixes for all the vulnerable codes in your web application.


