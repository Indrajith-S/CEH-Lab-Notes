- An attacker knows that many different types of files can hold all sorts of hidden information and that tracking or finding these files can be an almost impossible task. Therefore, they use stenographic techniques to hide data. This allows them to retrieve messages from their home base and send back updates without a hint of malicious activity being detected.

- These messages can be placed in plain sight, and the servers that supply these files will never know they carry suspicious content. Finding these messages is like finding the proverbial “needle” in the World Wide Web haystack.

- Steganography is the art and science of writing hidden messages in such a way that no one other than the intended recipient knows of the message’s existence. Steganography is classified based on the cover medium used to hide the file. A professional ethical hacker or penetration tester must have a sound knowledge of various steganography techniques.

- Whitespace steganography is used to conceal messages in ASCII text by adding white spaces to the end of the lines. Because spaces and tabs are generally not visible in text viewers, the message is effectively hidden from casual observers. If the built-in encryption is used, the message cannot be read even if it is detected. To perform Whitespace steganography, various steganography tools such as snow are used. Snow is a program that conceals messages in text files by appending tabs and spaces to the end of lines, and that extracts hidden messages from files containing them. The user hides the data in the text file by appending sequences of up to seven spaces, interspersed with tabs.
- Navigate to **System Hacking\Steganography Tools\Whitespace Steganography Tools**, copy the **Snow** folder, and paste it on **Desktop**.
- Create a **Notepad** file, type **Hello World!**, and press **Enter**; then, long-press the **hyphen** key to draw a dashed line below the text. Save the file as **readme.txt** in the folder where **SNOW.EXE** (**C:\Users\Admin\Desktop\Snow**) is located.
- Open cmd
	> cd C:\Users\Admin\Desktop\Snow 
	> snow -C -m "some random hidden text" -p "magic" readme.txt readme2.txt
	
		- (Here, **magic** is the password, but you can type your desired password. **readme2.txt** is the name of the file that will automatically be created in the same location.)
		- Now, the data (“some random hidden text”) is hidden inside the **readme2.txt** file with the contents of **readme.txt**.
	> snow -C -p "magic" readme2.txt (It will show the content of readme.txt (the password is magic, which was entered while hiding the data)
	
	- To check the file in the GUI, open the **readme2.txt** in **Notepad**, and go to **Edit** --> **Select All**. You will see the hidden data inside **readme2.txt** in the form of spaces and tabs.