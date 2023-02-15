- A professional ethical hacker or pen tester must understand how to hide files using NTFS (NT file system or New Technology File System) streams. NTFS is a file system that stores any file with the help of two data streams, called NTFS data streams, along with file attributes. The first data stream stores the security descriptor for the file to be stored such as permissions; the second stores the data within a file. Alternate data streams are another type of named data stream that can be present within each file.
- Now, go to the **C:** drive, create a **New Folder**, and name it **magic**.
- Navigate to the location **C:\Windows\System32**, copy **calc.exe**, and paste it to the **C:\magic** location.
- open cmd
	> cd C:\ 
	> cd magic
	> notepad readme.txt (to create a new file in magic)
	> type something in it (hello world)
	> dir (This action lists all the files present in the directory, along with their file sizes. Note the file size of **readme.txt**)
	> c:\magic\calc.exe > c:\magic\readme.txt:calc.exe (This command will hide **calc.exe** inside the **readme.txt**)
	> dir (note that the size of readme.txt hasn't changed)
	> 

- Navigate to the directory **C:\magic** and delete **calc.exe**.
	> mklink backdoor.exe readme.txt:calc.exe
	> backdoor.exe (to execute the calculator program)

	- For demonstration purposes, we are using the same machine to execute and hide files using NTFS streams. In real-time, attackers may hide malicious files in the target system and keep them invisible from the legitimate users by using NTFS streams, and may remotely execute them whenever required.
	- 