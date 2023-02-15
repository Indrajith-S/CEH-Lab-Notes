- Social engineers exploit human behavior (manners, enthusiasm toward work, laziness, innocence, etc.) to gain access to the information resources of the target company. This information is difficult to be guarded against social engineering attacks, as the victim may not be aware that he or she has been deceived. The attacks performed are similar to those used to extract a company’s valuable data. To guard against social engineering attacks, a company must evaluate the risk of different types of attacks, estimate the possible losses, and spread awareness among its employees.

- As a professional ethical hacker or pen tester, you must perform phishing attacks in the organization to assess the awareness of its employees.

- As an administrator or penetration tester, you may have implemented highly sophisticated and expensive technology solutions; however, all these techniques can be bypassed if the employees fall prey to simple social engineering scams. Thus, employees must be educated about the best practices for protecting the organization’s systems and information.

### Audit Organization's Security for Phishing Attacks using OhPhish

- OhPhish is a web-based portal for testing employees’ susceptibility to social engineering attacks. It is a phishing simulation tool that provides an organization with a platform to launch phishing simulation campaigns on its employees. The platform captures the responses and provides MIS reports and trends (on a real-time basis) that can be tracked according to the user, department, or designation.

- Here, we will audit the organization’s security infrastructure for phishing attacks using OhPhish.
- Go to **https://portal.ohphish.com/login**
- In the OhPhish **Dashboard**, click on the **Entice to Click** option.
- The **Create New Email Phishing Campaign** form appears.
- In the **Campaign Name** field, enter any name (here, **Test - Entice to Click**). In the **Select Template Category** field, select **Coronavirus/COVID-19** from the drop-down list.
	- Ensure that the **Existing Template** is selected in the **Email Template** option.
- In the **Select Country** field, leave the default option selected (**All**).
- In the **Select Template** field, click the **Select Template** button and select **Corona Virus Advisory** from the drop-down list.
- Click the **Select** button in the **Select Template** field to select the template.
	- The **template selected** notification appears below the **Select Template** field.
- Leave fields such as **Sender Email**, **Sender Name**, **Subject**, **Select Time Zone**, **Expiry Date**, and **Schedule Later** set to their default values.
- In the **Import users** field, click **Select Source**.
- **Import Users** pop-up appears, click to select **Quick Add** option from the list of options.
- The **Import Users Info** pop-up appears; enter the details of the employee and click **Add**.
- Similarly, you can add the details of multiple users. Here, we added two users.
- In the **Batch Count** and **Batch Interval** fields, set the values to **1**.
	- Batch Count**: indicates how many you want to send emails to at one time; **Batch Interval**: indicates at what interval (in minutes) you want to send emails to a batch of users.
	- The values of Batch Count and Batch Interval might differ depending on the number of users you are sending phishing emails to.
- Leave the **Landing Page** field set to its default value.
- Now, scroll down to the end of the page and click **Create** to create the phishing campaign.
- Now we wait for the phishing to take place
- Click on the **Test – Entice to Click** campaign present on the **OhPhish Dashboard**.
- The **Campaign Detailed Report** page appears, displaying the **Campaign Details** and **Campaign Summary** sections.
- In the **Campaign Summary** section, you can observe that the values of **No. of targets who have clicked the link (defaulters)** and **No. of Targets who have opened the mail** are both **1** (here, we have opened only one email account).
- In the **Campaign Summary** section, you can observe that the value of **No. of targets who have clicked the link (defaulters)** is **1**. Click on **1** icon to see the defaulter.
- The **Campaigns Users** page appears, displaying the details of the defaulter, such as **Risk Score**, **Credentials**, **IP Address**, **Location**, etc.,.
- Now, click to expand the **Reports** section in the left pane and select the **Executive Summary Report** option.
- The **Campaign Report** page appears; select any phishing campaign from the drop-down list (here, **Test – Send to Attachment**) and click on the **Export** icon to export the report.
- This way we can do the same for others too, like, Send Attachment option available on the dashboard.