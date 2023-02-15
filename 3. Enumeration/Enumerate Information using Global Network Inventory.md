- Using Global Network Inventory application
- The **New Audit Wizard** window appears; click **Next**.
- Under the **Audit Scan Mode** section, click the **Single address scan** radio button, and then click **Next**.
- Under the **Single Address Scan** section, specify the target IP address in the **Name** field of the **Single address** option (in this example, the target IP address is **10.10.10.16**); Click **Next**.
- The next section is **Authentication Settings**; select the **Connect as** radio button and enter the **Windows Server 2016** machine credentials (Domain\Username: **Administrator** and Password: **Pa$$w0rd), and then click Next.
	- In reality, attackers do not know the credentials of the remote machine(s). In this situation, they choose the **Connect as currently logged on user** option and perform a scan to determine which machines are active in the network. With this option, they will not be able to extract all the information about the target system. Because this lab is just for assessment purposes, we have entered the credentials of the remote machine directly.

- In the final step of the wizard, leave the default settings unchanged and click **Finish**.
