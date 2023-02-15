- Burp Suite is an integrated platform for performing security testing of web applications. It has various tools that work together to support the entire testing process from the initial mapping and analysis of an application’s attack surface to finding and exploiting security vulnerabilities. Burp Suite contains key components such as an intercepting proxy, application-aware spider, advanced web application scanner, intruder tool, repeater tool, and sequencer tool.

- Here, we will perform a brute-force attack on the target website using Burp Suite.
1.  Click the **Firefox** icon from the top section of **Desktop** to launch the **Mozilla Firefox** browser.
    
2.  The **Mozilla Firefox** window appears; type **http://10.10.10.16:8080/CEH/wp-login.php?** Into the address bar and press **Enter**.
    
    > Here, we will perform a brute-force attack on the designated WordPress website hosted by the **Windows Server 2016** machine.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab73327/screens/wjurvsz0.jpg)
    
3.  Now, we shall set up a **Burp Suite** proxy by first configuring the proxy settings of the browser.
    
4.  In the **Mozilla Firefox** browser, click the **Open menu** icon in the right corner of the menu bar and select **Preferences** from the list.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab73327/screens/0z1fq1jf.jpg)
    
5.  The **General** settings tab appears. In the **Find in Preferences** search bar, type **proxy**, and press **Enter**.
    
6.  The **Search Results** appear. Click the **Settings** button under the **Network Settings** option.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab73327/screens/i52leezc.jpg)
    
7.  The **Connection Settings** window appears; select the **Manual proxy configuration** radio button and specify the **HTTP Proxy** as **127.0.0.1** and the **Port** as **8080**. Tick the **Use this proxy server for all protocols** checkbox and click **OK**. Close the **Preferences** tab and minimize the browser window.
    
    ![2020-08-26_15-54-16.jpg](https://labondemand.blob.core.windows.net/content/lab73327/2020-08-26_15-54-16.jpg)
    
8.  Now, minimize the browser window, click the **Applications** menu form the top left corner of **Desktop**, and navigate to **Pentesting** --> **Web Application Analysis** --> **Web Application Proxies** --> **burpsuite** to launch the **Burp Suite** application.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab73327/screens/hy3pesop.jpg)
    
9.  A security pop-up appears, enter the password as **toor** in the **Password** field and click **OK**.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab73327/screens/s5sbfxgd.jpg)
    
10.  In the next **Burp Suite Community Edition** notification, click **OK**.
    
11.  In the **Terms and Conditions** wizard, click the **I Accept** button.
    
    > If **Delete old temporary files?** pop-up appears, click **Delete**.
    
12.  The **Burp Suite** main window appears; ensure that the **Temporary project** radio button is selected and click the **Next** button, as shown in the screenshot.
    
    > If an update window appears, click **Close**.
    
13.  In the next window, select the **Use Burp defaults** radio-button and click the **Start Burp** button.

14.  The **Burp Suite** main window appears; click the **Proxy** tab from the available options in the top section of the window.
 
15.  In the **Proxy** settings, by default, the **Intercept** tab opens-up. Observe that by default, the interception is active as the button says **Intercept is on**. Leave it running.
    
    > Turn the interception on if it is off.
    
16.  Switch back to the browser window. On the login page of the target WordPress website, type random credentials, here **admin** and **password**. Click the **Log In** button.
    
    > You can enter the credentials of your choice here.
    
17.  Switch back to the **Burp Suite** window; observe that the HTTP request was intercepted by the application.
    
18.  Now, right-click anywhere on the HTTP request window, and from the context menu, click **Send to Intruder**.
    
    > Observe that Burp Suite intercepted the entered login credentials.
    
    > If you do not get the request as shown in the screenshot, then press the **Forward** button.
    > 
19.  Now, click on the **Intruder** tab from the toolbar and observe that under the **Intruder** tab, the **Target** tab appears by default.
    
20.  Observe the target host and port values in the **Host** and **Port** fields.

    
21.  Click on the **Positions** tab under the **Intruder** tab and observe that Burp Suite sets the target positions by default, as shown in the HTTP request. Click the **Clear §** button from the right-pane to clear the default payload values.

22.  Once you clear the default payload values, select **Cluster bomb** from the **Attack type** drop-down list.
    
    > Cluster bomb uses multiple payload sets. There is a different payload set for each defined position (up to a maximum of 20). The attack iterates through each payload set in turn so that all permutations of payload combinations are tested. For example, if there are two payload positions, the attack will place the first payload from payload set 2 into position 2 and iterate through all payloads in payload set 1 in position 1; it will then place the second payload from payload set 2 into position 2 and iterate through all the payloads in payload set 1 in position 1.

23.  Now, we will set the username and password as the payload values. To do so, select the username value entered in **Step 17** and click **Add §** from the left-pane.
    
24.  Similarly, select the password value entered in **Step 17** and click **Add §** from the left-pane.
    
    > Here, the username and password are **admin** and **password**.

25.  Once the username and password payloads are added. The symbol **‘§’** will be added at the start and end of the selected payload values. Here, as the screenshot shows, the values are **admin** and **password**.

26.  Navigate to the **Payloads** tab under the **Intruder** tab and ensure that under the **Payload Sets** section, the **Payload set** is selected as **1**, and the **Payload type** is selected as **Simple list**.
    
27.  Under the **Payload Options [Simple list]** section, click the **Load…** button.

    
28.  A file selection window appears; navigate to the location **/home/attacker/Desktop/CEHv11 Module 14 Hacking Web Applications/Wordlist**, select the **username.txt** file, and click the **Open** button.

    
29.  Observe that the selected **username.txt** file content appears under the **Payload Options [Simple list]** section, as shown in the screenshot.

30.  Similarly, load a password file for the payload set 2. To do so, under the Payload Sets section, select the **Payload set** as **2** from the drop-down options and ensure that the **Payload type** is selected as **Simple list**.
    
31.  Under the **Payload Options [Simple list]** section, click the **Load…** button.
    
32.  A file selection window appears; navigate to the location **/home/attacker/Desktop/CEHv11 Module 14 Hacking Web Applications/Wordlist**, select the **password.txt** file, and click the **Open** button.

33.  Observe that selected **password.txt** file content appears under the **Payload Options [Simple list]** section, as shown in the screenshot.

34.  Once the wordlist files are selected as payload values, click the **Start attack** button to launch the attack.

35.  A **Burp Intruder** notification appears. Click **OK** to proceed.
    
36.  The **Intruder attack 1** window appears as the brute-attack initializes. It displays various username-password combinations along with the **Length** of the response and the **Status**.
    
37.  Wait for the progress bar at the bottom of the window to complete.

38.  After the progress bar completes, scroll down and observe the different values of **Status** and **Length**. Here, Status=**302** and Length= **1105**.
    
    > Different values of Status and Length indicate that the combination of the respective credentials is successful.
    
    > The values might differ in your lab environment.
    
39.  In the **Raw** tab under the **Request** tab, the HTTP request with a set of the correct credentials is displayed. (here, username=**admin** and password=**qwerty@123**), as shown in the screenshot. Note down these user credentials.

40.  Now, that you have obtained the correct user credentials, close the **Intruder attack 1** window.
    
    > If a **Warning** pop-up appears, click **OK**.
    
41.  Navigate back to the **Proxy** tab and click the **Intercept is on** button to turn off the interception. The **Intercept is on** button toggles to **Intercept is off**, indicating that the interception is off.

42.  Switch to the browser window and perform **Steps 5-7**. Remove the browser proxy set up in **Step 8**, by selecting the **No proxy** radio-button in the **Connection Settings** window and click **OK**. Close the tab.

43.  Reload the target website **http://10.10.10.16:8080/CEH/wp-login.php?**, enter the **Username** and **Password** obtained in **Step 40** and click **Log In**.
    
    > Here, the username and password are **admin** and **qwerty@123**.
    
    > If a pop-up appears, click **Resend**.
    
44.  You are successfully logged in using the brute-forced credentials. The **Welcome to WordPress!** Page appears, as shown in the screenshot.