- Uniscan is a versatile server fingerprinting tool that not only performs simple commands like ping, traceroute, and nslookup, but also does static, dynamic, and stress checks on a web server. Apart from scanning websites, uniscan also performs automated Bing and Google searches on provided IPs. Uniscan takes all of this data and combines them into a comprehensive report file for the user.
- Open Terminal
	> sudo su
	> cd
	> uniscan -h
	> uniscan -u http:// #targetip:8080/ #domain -q
	- the **-u** switch is used to provide the target URL, and the **-q** switch is used to scan the directories in the web server.
	- Uniscan starts performing different tests on the webserver and discovering **web directories**
		- Scroll to analyze the complete output of the scan.

	- Now, run uniscan using two options together. Here **-w** and **-e** are used together to enable the file check (**robots.txt** and **sitemap.xml** file).
	> uniscan -u http:// #targetip:8080/ #domain -we
	- Uniscan starts the file check and displays the results.
		- Scroll to analyze the complete scan result.


- click **usr** --> **share** --> **uniscan** --> **report**.
- Right-click on #targetip .html. Hover your mouse cursor on **Open With** and click **Firefox** from the menu to view the scan report.
- The report opens in the browser, giving you all **scan details** in a more comprehensive manner.
