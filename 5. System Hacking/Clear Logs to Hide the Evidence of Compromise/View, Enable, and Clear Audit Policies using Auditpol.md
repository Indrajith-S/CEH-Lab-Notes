- Auditpol.exe is the command-line utility tool to change the Audit Security settings at the category and sub-category levels. You can use Auditpol to enable or disable security auditing on local or remote systems and to adjust the audit criteria for different categories of security events.

- In real-time, the moment intruders gain administrative privileges, they disable auditing with the help of auditpol.exe. Once they complete their mission, they turn auditing back on by using the same tool (audit.exe).
- Open Cmd as administrator
	> auditpol /get /category:* (to view all the audit policies)
	> auditpol /set /category:"system","account logon" /success:enable /failure:enable (to enable the audit policies)
	> auditpol /get /category:* (to check whether the audit policies are enabled)
	> auditpol /clear /y (to clear the audit policies)
	> auditpol /get /category:* (to check whether audit policies are cleared or not)

		- **No Auditing** indicates that the system is not logging audit policies.
		- For demonstration purposes, we are clearing logs on the same machine. In real-time, the attacker performs this process after gaining access to the target system to clear traces of their malicious activities from the target system.
