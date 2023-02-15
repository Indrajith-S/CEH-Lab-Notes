- A web parameter tampering attack involves the manipulation of parameters exchanged between the client and server to modify application data such as user credentials and permissions, price, and quantity of products.

- Here, we will use the Burp Suite tool to perform parameter tampering.
- Follow the first few steps regarding switching the proxy on and launching burpsuite.

1.  The **Burp Suite** main window appears; click the **Proxy** tab from the available options in the top section of the window.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab73327/screens/uc5ngu1e.jpg)
    
2.  In the **Proxy** settings, by default, the **Intercept** tab opens-up. Observe that by default, the interception is active as the button says **Intercept is on**. Leave it running.
    
    > Turn the interception on if it is off.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab73327/screens/uxxdhltv.jpg)
    
3.  Switch back to the browser window, and on the login page of the target website (**www.moviescope.com**), enter the credentials **sam** and **test**. Click the **Log In** button.
    
    > Here, we are logging in as a registered user on the website.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab73327/screens/phy3bvai.jpg)
    
4.  Switch back to the **Burp Suite** window and observe that the HTTP request was intercepted by the application.
    
    > You can observe that the entered login credentials were intercepted by the Burp Suite.
    
5.  Now, keep clicking the **Forward** button until you are logged into the user account.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab73327/screens/v5n3zqx3.jpg)
    
6.  Switch to the browser, and observe that you are now logged into the user account, as shown in the screenshot.
    
7.  Now, click the **View Profile** tab from the menu bar to view the user information.
    
    ![Screenshot](https://labondemand.blob.core.windows.net/content/lab73327/screens/pn3o4vyh.jpg)
    
8.  After clicking the **View Profile** tab, switch back to the **Burp Suite** window and keep clicking the **Forward** button until you get the HTTP request, as shown in the screenshot.
    
9.  Now, navigate to the **Params** tab under the **Intercept** tab to view the captured parameters.
    
    ![2020-08-26_17-20-11.jpg](https://labondemand.blob.core.windows.net/content/lab73327/2020-08-26_17-20-11.jpg)
    
10.  Under the **Params** tab, observe a table with captured values such as **URL** and **Cookie**.
    
11.  In the **URL** type with the name **id**, double-click the **Value** column to change it from **1** to **2**, as shown in the screenshot.

12.  After changing the value, navigate back to the **Raw** tab.

13.  In the **Raw** tab, click the **Intercept is on** button to turn off the interception.

14.  After switching off the interception, navigate back to the browser window and observe that the user account associated with **ID=2** appears with the name **John**, as shown in the screenshot.
    
    > Although we logged in using sam as a username with ID=1, using Burp Suite, we successfully tampered with the ID parameter to obtain information about other user accounts.
    
