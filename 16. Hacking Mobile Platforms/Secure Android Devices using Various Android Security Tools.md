- Like personal computers, mobile devices store sensitive data and are susceptible to various threats. Therefore, they should be properly secured in order to prevent the compromise or loss of confidential data, lessen the risk of various threats such as viruses and Trojans, and mitigate other forms of abuse. Strict measures and security tools are vital to strengthening the security of these devices.
- As a professional ethical hacker or penetration tester, you should scan for any unsecured settings on the mobile device you are assessing, and then take appropriate action to secure them. You must do this before hackers exploit these vulnerabilities by; for example, downloading sensitive data, committing a crime using your Android device as a launchpad, and ultimately endangering your business.


### Analyze a Malicious App using Online Android Analyzers

- Online Android analyzers allow you to scan Android APK packages and perform security analyses to detect vulnerabilities in particular apps. Some trusted online Android analyzers are Sixo Online APK Analyzer.
- In this task, we will analyze a malicious app using various online Android analyzers.
- Open Chrome and go to https://www.sisik.eu/apk-tool
- Click the **Drop APK here or click to select file** field to upload an APK file from the device.
	- Sixo Online APK Analyzer allows you to analyze various details about Android APK files. It can decompile binary XML files and resources.
- Scroll down to the **Requested Permissions** section to view information regarding the app’s requested permissions.
	- When an app wants to access resources or various device capabilities, it typically must request permission from the user to do so. Some permissions are granted by the user when installing the app and some need to be confirmed later while the app is running. The requested permissions are declared in the app’s AndroidManifest.xml file.
- Scroll down to the **AndroidManifest.xml** section, which consists of essential information about the APK file.
	- The manifest file contains important information about the app that is used by development tools, the Android system, and app stores. It contains the app’s package name, version information, declarations of app components, requested permissions, and other important data. It is serialized into a binary XML format and bundled inside the app’s APK file.
- You can also scroll down to view information about the app’s **APK Signature**, **App Source Code**, etc.



### Analyze a Malicious App using Quixxi Vulnerability Scanner

- Quixxi is an intelligent and integrated end-to-end mobile app security solution. This powerful tool is for developers to protect and monitor any mobile apps in minutes.
- Open Chrome and go to https://vulnerabilitytest.quixxi/com/#/
- The **Quixxi** website loads; click the **Drag and drop or click here to scan your app** field.
- After the scan finishes, the result appears under the **Vulnerability Scan Report: A Summary** section, listing the number of discovered vulnerabilities, risk threats, etc.
- Click to expand **Permissions Used** node to view the permissions.
- Scroll-down, click to expand **CERTIFICATION INFORMATION** node to view certification details.
- Scroll-down further to view the OWASP information such as **Issue**, **Severity**, **Assessment Status**, **CWE**, **Exploits**, etc.
- You can scroll-down and click on **GET FULL REPORT** button to generate a full report.


### Secure Android Devices from Malicious Apps using Malwarebytes Security

- Malwarebytes is an antimalware mobile tool that provides protection against malware, ransomware, and other growing threats to Android devices. It blocks, detects, and removes adware and malware; conducts privacy audits for all apps; and ensures safer browsing.
- Open **Malwarebytes** app.
- **Malwarebytes Security** initializes. A **Let’s get you started** message appears; click the **Get started** button to proceed.
- The **Your device is safe** screen loads; click the **Scan now** button to start scanning the system.
- After the completion of the scan, **Scan finished** message appears, click **View scan results** to see the results.
- A **Threats** screen appears. This will show you all the malware (if any) found on your device.
- Click the **Remove selected** button to remove the detected malware from your device.
- The Malwarebytes **Scanner** screen appears, notifying you that **All items have been dealt with!**.
- Click **Scan after update** in the lower section of the **Scanner** window under **Previous scans** to view details of the scan.
- The **Scanning history** screen appears, displaying the deleted malicious file.
