- The web applications that are available on the Internet may have vulnerabilities. Some hackers’ attack strategies may need the Administrator role on your server, but sometimes they simply need sensitive information about the server. Utilizing Nmap and http-enum.nse content returns a diagram of those applications, registries, and records uncovered. This way, it is possible to check for vulnerabilities or abuses in databases. Through this technique, it is possible to discover genuine (and extremely dumb) security imperfections on a site such as some sites (like WordPress and PrestaShop) that maintain accessibility to envelopes that ought to be erased once the task has been settled. Once you have identified a vulnerability, you can discover a fix for it.

- Nmap, along with Nmap Scripting Engine, can extract a lot of valuable information from the target web server. In addition to Nmap commands, Nmap Scripting Engine (NSE)provides scripts that reveal various useful information about the target web server to an attacker.
- Open Terminal
	> sudo su
	> cd
	
	- Enumerate the directories used by web servers and web applications, in the terminal window.
	> nmap -sV --script=http-enum #targeturl 
	- This script enumerates and provides you with the output details
	- The next step is to discover the hostnames that resolve the targeted domain.
	> nmap --script hostmap-bfk -script-args hostmap-bfk.prefix=hostmap- #targeturl 
	
	- Perform an HTTP trace on the targeted domain.
	> nmap --script http-trace -d #targeturl 
	- This script will detect a vulnerable server that uses the TRACE method by sending an HTTP TRACE request that shows if the method is enabled or not.

	- Now, check whether Web Application Firewall is configured on the target host or domain.
	> nmap -p80 --script http-waf-detect #targeturl 
	- This command will scan the host and attempt to determine whether a web server is being monitored by an IPS, IDS, or WAF.
	- This command will probe the target host with malicious payloads and detect the changes in the response code.
