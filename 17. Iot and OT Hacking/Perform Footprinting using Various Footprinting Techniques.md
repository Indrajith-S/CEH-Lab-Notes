- As a professional ethical hacker or pen tester, your first step is to gather maximum information about the target IoT and OT devices by performing footprinting through search engines, advanced Google hacking, Whois lookup, etc.
- The first step in IoT and OT device hacking is to extract information such as IP address, protocols used (MQTT, ModBus, ZigBee, BLE, 5G, IPv6LoWPAN, etc.), open ports, device type, geolocation of the device, manufacturing number, and manufacturer of the device.
- Footprinting techniques are used to collect basic information about the target IoT and OT platforms to exploit them. Information collected through footprinting techniques includes IP address, hostname, ISP, device location, banner of the target IoT device, FCC ID information, certification granted to the device, etc.



### Gather Information using Online Footprinting Tools

- The information regarding the target IoT and OT devices can be acquired using various online sources such as Whois domain lookup, advanced Google hacking, and Shodan search engine. The gathered information can be used to scan the devices for vulnerabilities and further exploit them to launch attacks.
	- In this task, we will focus on performing footprinting on the MQTT protocol, which is a machine-to-machine (M2M)/“Internet of Things” connectivity protocol. It is useful for connections with remote locations where a small code footprint is required and/or network bandwidth is at a premium.
- Open chrome and go to https://www.whois.com/whois/
	- type www.oasis-open.org
	- Oasis is an organization that has published the MQTT v5.0 standard, which represents a significant leap in the refinement and capability of the messaging protocol that already powers IoT.
	- The result appears, displaying the following information: Domain Information, Registrant Contact, and Raw Whois Data.
	- This information is about the organization that has developed the MQTT protocol, and it might help keep track of the modifications and version changes of the target protocol.

- SCADA (**supervisory control and data acquisition**) is a category of software applications for controlling industrial processes, which is the gathering of data in real time from remote locations in order to control equipment and conditions.
- Open chrome and go to https://www.exploit-db.com/google-hacking-database
	- type **SCADA** in the **Quick Search** field and press **Enter**.
	- Now, we will use the dorks obtained in the previous step to query results in Google.
	- open a new tab and go to google.com
	- In the search field, type **"login" intitle:"scada login**" and click the **Google Search** button.
	- The search result appears; click any link (here, **SCADA :: seamtec SCADA login ::**).
		- Advanced Google hacking refers to the art of creating complex search engine queries by employing advanced Google operators to extract sensitive or hidden information about a target company from the Google search results.
	- In the login form, you can brute-force the credentials to gain access to the target SCADA system.
	- Similarly, you can use advanced search operators such as **intitle:"index of" scada** to search sensitive SCADA directories that are exposed on sites.


- Open chrome and go to https://account.shodan.io/login
- The **Login with Shodan** page appears; login to Shodan.
- Click **Shodan** in the top-left corner of the window.
- The **Shodan** main page appears; type **port:1883** in the address bar and press **Enter**.
	- Port 1883 is the default MQTT port; 1883 is defined by IANA as MQTT over TCP.
- The result appears, displaying the list of IP addresses having port 1883 enabled.
- Click on any IP address to view its detailed information.
- Detailed results for the selected IP address appears, displaying information regarding **Ports, Services, Hostnames, ASN**, etc.
- Similarly, you can gather additional information on a target device using the following Shodan filters:

	- **Search for Modbus-enabled ICS/SCADA systems:**
	    - port:502
	- **Search for SCADA systems using PLC name:**
	    - “Schneider Electric” 
	- **Search for SCADA systems using geolocation:**
	   - SCADA Country:"US"

- Using Shodan, you can obtain the details of SCADA systems that are used in water treatment plants, nuclear power plants, HVAC systems, electrical transmission systems, home heating systems, etc.