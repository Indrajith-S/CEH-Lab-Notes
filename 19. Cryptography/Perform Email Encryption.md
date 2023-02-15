- Currently, the majority of businesses use email as their primary source of communication, as it is simple and easy to communicate or share information. Emails can contain sensitive information about an organization such as projects, upcoming news, and financial data, which, when accessed by the wrong person, can cause huge losses to the organization. One can protect emails containing sensitive information by encrypting them.
- As a professional ethical hacker and penetration tester, you must have proper knowledge of encrypting email messages so that sensitive information sent through emails remain intact.


#### **Overview of Email Encryption**

- Email encryption hides the email content from eavesdroppers by encrypting it into an unreadable form. Emails can be encrypted and decrypted by means of a digital signature mechanism that uses public and private keys: the public key is shared, while the private key is kept private.

- There are numerous methods that can be employed for email encryption, including:

	- **Digital Signature**: Uses asymmetric cryptography to simulate the security properties of a signature in digital, rather than written form
	- **Secure Sockets Layer (SSL)**: Uses RSA asymmetric (public key) encryption to encrypt data transferred over SSL connections
	- **Transport Layer Security (TLS)**: Uses a symmetric key for bulk encryption, an asymmetric key for authentication and key exchange, and message authentication codes for message integrity
	- **Pretty Good Privacy (PGP)**: Used to encrypt and decrypt data that provides authentication and cryptographic privacy
	- **GNU Privacy Guard (GPG)**: Software replacement of PGP and free implementation of the OpenPGP standard that is used to encrypt and decrypt data


### Perform Email Encryption using RMail

- RMail is an email security tool that provides open tracking, proof of delivery, email encryption, electronic signatures, large file transfer functionality, etc. RMail works seamlessly with users’ existing email platforms, including Microsoft Outlook and Gmail, amongst others. Using this tool, you can encrypt sensitive emails and attachments for security or legal compliance.
- Launch any web browser, and go to https://www.rmail.com/free-trial/.
- The **RMail FREE TRIAL** webpage appears, click on **Apps** from the menu to navigate to the Apps page.
- In the **Get Started with Rmail. Select an App** page scroll down and select **RMail Online**.
- The **Rmail Online for Desktop & Mobile Browsers** window appears, scroll down and click on **CLICK HERE TO GET STARTED**.
- The **RMail** webpage appears, click on **CREATE AN ACCOUNT**.
- **Let's get started!** page appears, as well as the registration form. Fill in the required personal details and click on **Sign up** and activate the account.
- In the **Welcome back!** page, enter the email address and password that was used during registration and click on **Sign in**.
- The RMail Online page appears, in the **To** field enter the recepient address. Ensure that **Marked as** is selected under **Track & Prove** section in the right-pane. Check the **Encrypt - select primary receiving experience** option and ensure that the **Transmission-auto-decrypts for receiver** radio button is selected. Ensure that **E-Sign - send for signature** check-box is checked, and **Web Sign** radio button is selected.
- After selecting the options, enter a message to be sent to the recipient, and click on **SEND REGISTERED** button.
- Now, navigate to the tab in which Gmail account that was opened previously, you can observe an **Acknowledgement** email with **Proof of Sending**.
- In this task, for the purpose of demonstration, we will open the recipient’s account and view the email.
- You can observe that the email received is tagged as a registered email wherein a document has been sent for the recipient to review and electronically sign to confirm his/her identity.
- Click the **View & Sign Document** button to sign an agreement.
- A new **E-Sign** webpage appears displaying the email content; click **CONTINUE**.
- The **Instructions: How To E-Sign** page appears; read the instructions carefully and click **CONTINUE**.
- After viewing the email content, click **NEXT**.
- The **Final Step - Please Complete the Information Below** page appears with the **Document Signature** form. In the **Please enter your name** field, enter your name (Recipient’s name) and leave the **Initials** and **Title** field as blank and click the **Click to Sign** button.
- The **YOU’RE ALL DONE!** page appears; close the current tab to return to the opened email. Click **Inbox** from the left-hand pane to navigate to the inbox.
- Open an email from **RPost eSignOff Service**. You can observe that it is an acknowledgment email from RPost along with various details such as **Signed By, Date, Time, Original Recipient, IP, Message** **Id**, etc.
- In the sender's mail,  in **Inbox**, you can observe two emails (**Receipt** and **RPost eSignOff Service**). Click to open the **Receipt** email.
- The **Receipt** email contains information about the **Delivery Status**, **Message Envelope**, and **Message Statistics** of the sent email.
- The **Receipt** email also includes the **DeliveryReceipt** and **HtmlReceipt** attachments containing detailed information regarding the sent email.
- Now, navigate back to the **Inbox** and open an email from **RPost eSignOff Service**. This email contains the same information as the email received from **RPost eSignOff Service** by the recipient.