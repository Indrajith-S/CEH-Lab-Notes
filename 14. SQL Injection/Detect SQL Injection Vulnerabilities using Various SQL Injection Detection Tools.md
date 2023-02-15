### Detect SQL Injection Vulnerabilities using DSSS

- Damn Small SQLi Scanner (DSSS) is a fully functional SQL injection vulnerability scanner that supports GET and POST parameters. DSSS scans web applications for various SQL injection vulnerabilities.

- Here, we will use DSSS to detect SQL injection vulnerabilities in a web application.
- Open Terminal
	> sudo su
	> cd
	> cd DSSS (to navigate to the DSSS folder which is alredy downloaded)
	> python3 dsss.py (to view a list of available options in the DSSS application)
	
- Now browse to www.moviescope.com and login.
- Once you are logged into the website, click the **View Profile** tab from the menu bar; and when the page has loaded, make a note of the URL in the address bar of the browser.
- Right-click anywhere on the webpage and click **Inspect Element (Q)** from the context menu.
- The **Developer Tools** frame appears in the lower section of the browser window. Click the **Console** tab, type **document.cookie** in the lower-left corner of the browser, and press **Enter**.
- Select the cookie value, then right-click and copy it.
- Switch back to Terminal
	> python3 dsss.py -u "http://www.moviescope.com/viewprofile.aspx?id=1" --cookie=" #copiedcookie "
	- In this command, **-u** specifies the target URL and **--cookie** specifies the HTTP cookie header value.
	- The above command causes DSSS to scan the target website for SQL injection vulnerabilities.
	- The result appears, showing that the target website (**www.moviescope.com**) is vulnerable to blind SQL injection attacks. The vulnerable link is also displayed.

- In real life, attackers use blind SQL injection to access or destroy sensitive data. Attackers can steal data by asking a series of true or false questions through SQL statements. The results of the injection are not visible to the attacker. This type of attack can become time-intensive, because the database must generate a new statement for each newly recovered bit.



### Detect SQL Injection Vulnerabilities using OWASP ZAP

- OWASP Zed Attack Proxy (ZAP) is an integrated penetration testing tool for finding vulnerabilities in web applications. It offers automated scanners and a set of tools that allow you to find security vulnerabilities manually. It is designed to be used by people with a wide range of security experience, and as such is ideal for developers and functional testers who are new to penetration testing.

- In this task, we will use OWASP ZAP to test a web application for SQL injection vulnerabilities.
- Launch OWASP ZAP
- The **Automated Scan** wizard appears, enter the target website in the **URL to attack** field. Leave other options set to default, and then click the **Attack** button.
- **OWASP ZAP** starts performing **Active Scan** on the target website.
- After the scan completes, **Alerts** tab appears.
- You can observe the vulnerabilities found on the website under the **Alerts** tab.
- Now, expand the **SQL Injection** vulnerability node under the **Alerts** tab.
- Click on the discovered **SQL Injection** vulnerability and further click on the vulnerable URL.
- You can observe the information such as **Risk**, **Confidence**, **Parameter**, **Attack**, etc., regarding the discovered SQL Injection vulnerability in the lower right-bottom.
	- The risks associated with the vulnerability are categorized according to severity of risk as Low, Medium, High, and Informational alerts. Each level of risk is represented by a different flag color:
		- **Red Flag**: High risk
		- **Orange Flag**: Medium risk
		- **Yellow Flag**: Low risk
		- **Blue Flag**: Provides details about information disclosure vulnerabilities
- 