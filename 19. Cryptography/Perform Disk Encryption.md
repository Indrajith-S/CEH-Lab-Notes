- Disk encryption is a technology that protects the confidentiality of the data stored on a disk by converting it into an unreadable code using disk encryption software or hardware, thus preventing unauthorized users from accessing it. Disk encryption provides confidentiality and privacy using passphrases and hidden volumes. As a professional ethical hacker or pen tester, you should perform disk encryption in order to prevent sensitive information from unauthorized access.
- Disk encryption works in a manner similar to text-message encryption and protects data even when the OS is not active. By using an encryption program for the user’s disk (Blue Ray, DVD, USB flash drive, External HDD, and Backup), the user can safeguard any or all information burned onto the disk and thus prevent it from falling into the wrong hands. Disk-encryption software scrambles the information burned on the disk into an illegible code. It is only after decryption of the disk information that one can read and use it.


### Perform Disk Encryption using VeraCrypt

- VeraCrypt is a software used for establishing and maintaining an on-the-fly-encrypted volume (data storage device). On-the-fly encryption means that data is automatically encrypted just before it is saved, and decrypted just after it is loaded, without any user intervention. No data stored on an encrypted volume can be read (decrypted) without using the correct password/keyfile(s) or correct encryption keys. The entire file system is encrypted (e.g., file names, folder names, free space, metadata, etc.).
- Open VeraCrypt
- The **VeraCrypt** main window appears; click the **Create Volume** button.
- The **VeraCrypt Volume Creation Wizard** window appears. Ensure that the **Create an encrypted file container** radio-button is selected and click **Next** to proceed.
- In the **Volume Type** wizard, keep the default settings and click **Next**.
- In the **Volume Location** wizard, click **Select** **File…**.
- The **Specify Path and File Name** window appears; navigate to the desired location (here, **Desktop**), provide the **File name** as **My Volume**, and click **Save**.
- After saving the file, the location of a file containing the **VeraCrypt** volume appears under the **Volume Location** field; then, click **Next**.
- In the **Encryption Options** wizard, keep the default settings and click **Next**.
- In the **Volume Size** wizard, ensure that the **MB** radio-button is selected and specify the size of the VeraCrypt container as **5**(menton the size you want); then, click **Next**.
- The **Volume Password** wizard appears; provide a strong password in the **Password** field, retype in the **Confirm** field, and click **Next**.
- The **Volume Format** wizard appears; ensure that **FAT** is selected in the **Filesystem** option and **Default** is selected in **Cluster** option.
- Check the checkbox under the **Random Pool, Header Key**, and **Master Key** section.
- Move your mouse as randomly as possible within the **Volume Creation Wizard** window for at least **30 seconds** and click the **Format** button.
- After clicking **Format**, VeraCrypt will create a file called **My Volume** in the provided folder. This file depends on the VeraCrypt container (it will contain the encrypted VeraCrypt volume).
- Depending on the size of the volume, volume creation may take some time.
- The **VeraCrypt** main window appears; select a drive and click **Select File…**.
- The **Select a VeraCrypt Volume** window appears; navigate to **Desktop**, click **My Volume**, and click **Open**.
- The window closes, and the **VeraCrypt** window appears displaying the location of selected **volume** under the Volume field; then, click **Mount**.
- The **Enter password** dialog-box appears; type the password you specified and click **OK**.
- After the password is verified, **VeraCrypt** will mount the volume in **I:** drive.
- **My Volume** has successfully mounted the container as a virtual disk (**I:**). The virtual disk is entirely encrypted (including file names, allocation tables, free space, etc.) and behaves similarly to a real disk. You can copy or move files to this virtual disk to encrypt them.
- Switch to the **VeraCrypt** window, click **Dismount**, and then click **Exit**.
- The drive located in **This PC** disappears.
	- This lab is used to demonstrate that, in cases of system hacks, if an attacker manages to gain remote access or complete access to the machine, he/she will not be able to find the encrypted volume—including its files—unless he/she is able to obtain the password. Thus, all sensitive information located on the encrypted volume is safeguarded.


### Perform Disk Encryption using BitLocker Drive Encryption

- BitLocker provides offline-data and OS protection for your computer, and helps to ensure that data stored on a computer that is running Windows® is not revealed if the computer is tampered with when the installed OS is offline. BitLocker uses a microchip that is called a Trusted Platform Module (TPM) to provide enhanced protection for your data and to preserve early boot-component integrity. The TPM can help protect your data from theft or unauthorized viewing by encrypting the entire Windows volumes.
- Open Manage BitLocker
- Click the **Turn on BitLocker** option under any one of your drives.
- The **BitLocker Drive Encryption (D:)** wizard appears; check the **Use a password to unlock the drive** checkbox.
- Type the password in the **Enter your password** field and re-type the password in the **Reenter your password** field; then, click **Next**.
- The **How do you want to back up your recovery key?** step appears; click **Save to a file** from the available options.
- The **Save BitLocker recovery key as** window appears; keep the save location set to **This PC** --> **Documents** and click **Save**.
- Click **Next** in the **How do you want to back up your recovery key?** step.
- In the **Choose how much of your drive to encrypt** step, select the **Encrypt entire drive (slower but best for PCs and drives already in use)** button, and click **Next**.
- In the **Choose which encryption mode to use** step, ensure that the **Compatible mode (best for drives that can be moved from this device)** option is selected, and click **Next**
- In the **Are you ready to encrypt this drive?** step, click **Start encrypting** to encrypt the selected drive.
- After the completion of the encryption process, the **Encryption of D:** is complete notification appears; click **Close** and **Restart** the machine.



### Perform Disk Encryption using Rohos Disk Encryption

- Rohos Disk Encryption creates hidden and password-protected partitions on a computer or USB flash drive, and password protects/locks access to your Internet applications. It uses a NIST-approved AES encryption algorithm with a 256-bit encryption key length. Encryption is automatic and on-the-fly.
- Open Rohos
- The **Rohos Disk Encryption** main window appears; **click Create new disk…**
- The **Create new Rohos disk** window appears; click **Change…** to modify the size of the encrypted disk.
- Provide a password in the **Specify a new password to access the disk** field and retype it into the **Confirm password** field; then, click **Create disk** button.
- Wait until the encrypted volume is created. The time to create the encrypted volume depends upon the size you specified under the **Disk Size** option: if large, it will take a long time to create the volume.
- On creating the encrypted volume, the **Encrypted Disk (R:)** window appears, displaying the default disk content.
- The **Disk is connected** notification appears at the top section of the **Rohos Disk Encryption** window.
	- This drive appears only when you are connected to Rohos Disk Encryption, and disappears when you disconnect/exit.
- If you wish to conceal any important files/directories from anyone accessing your system, you can place them in this drive and access them whenever required (by launching Rohos and entering the password).
	- You can also use the Encrypt USB drive option to share sensible information with someone via USB. You can use this application to store the files in an encrypted disk and share the password with that person. The person with whom you want to share the files can access them only after entering the correct password. This way, you can protect the files from being viewed by a third person and thereby safeguard them.