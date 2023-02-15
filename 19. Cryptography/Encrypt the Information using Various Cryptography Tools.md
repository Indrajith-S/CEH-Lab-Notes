#### **Overview of Cryptography Tools**

- System administrators use cryptography tools to encrypt system data within their network to prevent attackers from modifying the data or misusing it in other ways. Cryptography tools can also be used to calculate or decrypt hash functions available in MD4, MD5, SHA-1, SHA-256, etc.

- Cryptography tools are used to convert the information present in plain text (readable format) into cipher text (unreadable format) using a key or encryption scheme. The converted data are in the form of a scrambled code that is encrypted and sent across a private or public network.


### Calculate One-way Hashes using HashCalc

- Hash functions calculate a unique fixed-size bit string representation, called a message digest, of any arbitrary block of information. Message digest (One-way Hash) functions distill the information contained in a file (small or large) into a single fixed-length number, typically between 128 and 256 bits. If any given bit of the function’s input is changed, every output bit has a 50% chance of changing. Given an input file and its corresponding message digest, it should be nearly impossible to find another file with the same message digest value, as it is computationally infeasible to have two files with the same message digest value.
- HashCalc enables you to compute multiple hashes, checksums, and HMACs for files, text, and hex strings. It supports the Secure Hash Algorithm family: MD2, MD4, MD5, SHA1, SHA2 (SHA256, SHA384, SHA512), RIPEMD160, PANAMA, TIGER, CRC32, ADLER32, and the hash used in the peer-to-peer file sharing applications, eDonkey and eMule.
- Navigate to **MD5 and MD6 Hash Calculators\HashCalc** and double click **setup.exe**.
- Open HashCalc
- In the **HashCalc** window; ensure that the **File** option is selected in the **Data Format** field and click ellipsis icon under the **Data** filed.
- The **Find** window appears, navigate to the location where you saved the **Test.txt** file (here, **Desktop**) and click **Open**.
	- Test.txt contains some text.
- The path of the selected file (**Test.txt**) appears under the **Data** field. Ensure that the **MD5, SHA1, RIPEMD160**, and **CRC32** hash functions are selected. Click the **Calculate** button.
- The calculated hash values of the **Test.txt** file appears.
	- In real-time, the HashCalc tool is used to check the integrity of a file where the changes in the hash values indicate that the file content has been modified.


### Calculate MD5 Hashes using MD5 Calculator

- MD2, MD4, MD5, and MD6 are message digest algorithms used in digital signature applications to compress documents securely before the system signs it with a private key. The algorithms can be of variable length, but the resulting message digest is always 128 bits.
- The MD5 algorithm is a widely used cryptographic hash function that takes a message of arbitrary length as input and outputs a 128-bit (16-byte) fingerprint or message digest of the input. The MD5 algorithm is used in a wide variety of cryptographic applications and is useful for digital signature applications, file integrity checking, and storing passwords.
- MD5 Calculator is a simple application that calculates the MD5 hash of a given file, and it can be used with large files (e.g., multiple gigabytes). It features a progress counter and a text field from which the final MD5 hash can be easily copied to the clipboard. MD5 calculator can be used to check the integrity of a file.
- Navigate to **MD5 and MD6 Hash Calculators\MD5 Calculator** and double-click **md5calc(1.0.0.0).msi**.
- Navigate to **Desktop**, right-click on the text file (**Test.txt**) that we created in the previous task, and click **MD5 Calculator** from the context menu to calculate the MD5 hash of the file.
- The **MD5 Calculator** window appears, with the path of file under the **File Name** field and MD5 hash value under the **MD5 Digest** field.
- Copy the MD5 hash value from the **MD5 Digest** field.
- Now, double-click the **Test.txt** file from **Desktop** to open it and change the content of the file by inserting text within. Save and close the **Test.txt** file.
- After changing the file content, again right-click on the text file (**Test.txt**) and click **MD5 Calculator** from the context menu to calculate the MD5 hash of the file.
- A new **MD5 Calculator** window appears, with the MD5 hash value under the **MD5 Digest** field. In the **Compare To** field, paste the copied MD5 hash value of the file before it was modified.
- The symbol (**<>**) between the **MD5 Digest** and **Compare To** fields indicates that the MD5 hash values of the file before modification is not equal to the MD5 hash value of the file after modification.
	- If a person wants to send a file to another person via a medium, they will calculate its hashes and send the file (along with the hash value) to the intended person. When the intended person receives the email, they will download the file and calculate its value using the MD5 Calculator.
	- The recipient compares the generated hash value with the hash value that was sent through email: if both tally, it is evident that they received the file without any modifications by a third person and that the integrity of the file is intact.


### Calculate MD5 Hashes using HashMyFiles

- HashMyFiles is a small utility that allows you to calculate the MD5 and SHA1 hashes of one or more files in your system: you can easily copy the MD5/SHA1 hashes list into the clipboard, or save them into text/html/xml file. HashMyFiles can also be launched from the context menu of Windows Explorer, and can display the MD5/SHA1 hashes of the selected file or folder.
- Navigate to **MD5 and MD6 Hash Calculators\HashMyFiles** and double-click **HashMyFiles.exe**.


### Perform File and Text Message Encryption using CryptoForge

- CryptoForge is a file encryption software for personal and professional data security. It allows you to protect the privacy of sensitive files, folders, or email messages by encrypting them with strong encryption algorithms. Once the information has been encrypted, it can be stored on insecure media or transmitted on an insecure network—such as the Internet—and remain private. Later, the information can be decrypted into its original form.
- Navigate to **Cryptography Tools\CryptoForge** and double-click **CryptoForge.exe**.
- Right click on any document and click on encrypt from the context menu.
- The **Enter Passphrase - CryptoForge Files** dialog-box appears; type a password in the **Passphrase** field, retype it in the **Confirm** field, and click **OK**. 
- Now, the file will be encrypted in the same location, and the old file will be deleted automatically.
	- No one can access this file unless the user provides the password for the encrypted file. You will have to share the password with the user through message, email, or any other means.


- So far, you have seen how to encrypt a file and share it with the intended user. Now, we shall share an encrypted message with a user.
- In your machine, click the **Start** icon present in the bottom-left corner of **Desktop** and click **CryptoForge Text** from the apps to launch the application.
- The **Enter Passphrase - CryptoForge Text** dialog-box appears; type a password in the **Passphrase** field, retype it in the **Confirm** field, and click **OK**. 
- Now, you need to save the file. Click **File** in the menu bar and click **Save**.
- Now, let us assume that you shared the file through the mapped network drive and shared the password to decrypt the file in an email message or through some other means.
- In real-time, you may share sensitive information through email by encrypting data using CryptoForge.


### Encrypt and Decrypt Data using BCTextEncoder

- BCTextEncoder simplifies encoding and decoding text data. Plain text data are compressed, encrypted, and converted to text format, which can then be easily copied to the clipboard or saved as a text file. This utility software uses public key encryption methods and password-based encryption, as well as strong and approved symmetric and public key algorithms for data encryption.
- Navigate to **ryptography Tools\BCTextEncoder** and double click **BCTextEncoder_v.1.03.2.1.exe** and open BCTextEncoder.
- To encrypt the text, insert text in the clipboard.

Or

Select the data that you want to encode and paste it to the clipboard by pressing **Ctrl+V**.

- Ensure that the **password** option is selected in the **Encode by** field and click **Encode**.
- **BCTextEncoder** encodes the text and displays it in under the **Encoded** **text** section.
	- In real-time, using this procedure, you can encode the text while sending it to the intended user along with the password used for encryption. The user for whom the text is intended should have the BCTextEncoder application installed on his/her machine. He/she will have to paste the encoded text into the **Encoded text** section and use the password you shared, to decode it to plain text.