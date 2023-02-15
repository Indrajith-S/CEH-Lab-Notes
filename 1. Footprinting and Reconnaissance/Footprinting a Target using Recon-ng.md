> recon-ng
> marketplace install all
> modules search

- You will be able to perform network discovery, exploitation, reconnaissance, etc. by loading the required modules.

> workspaces
> workspaces create CEH
> workspaces list

- Add a domain in which you want to perform network reconnaissance.

> db insert domains

> certifiedhacker.com
> show domains

- Harvest the hosts-related information associated with **certifiedhacker.com** by loading network reconnaissance modules such as brute_hosts, Netcraft, and Bing.

> modules load brute
> modules load recon/domains-hosts/brute_hosts
(to harvest hosts)
> run


- To resolve hosts using the Bing module, use the following commands:
	> back
	> modules load recon/domains-hosts/bing_domains_web
	> run
	
- Now, that you have harvested several hosts, we will prepare a report containing all the hosts.

> modules load reporting
> modules load reporting/html
> options set FILENAME /root/Desktop/results.html
> options set CREATOR Blackbody
> options set CUSTOMER certifiedhackerNetworks
> run

