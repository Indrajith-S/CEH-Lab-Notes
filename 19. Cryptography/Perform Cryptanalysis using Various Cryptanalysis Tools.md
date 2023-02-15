- Attackers tend to focus on easy to compromise targets. Therefore, in order to attain maximum network security, strong encryption is needed for all the traffic placed onto the transmission media, no matter the type and location: if an attacker wishes to break into an encrypted network, he/she faces decrypting a whole slew of encrypted packets, which is a difficult task. Therefore, the attacker is likely to try and find another target that is easy to compromise or will simply abort the attempt. Using the latest encryption algorithms provides a strong layer of security to an organization.

- As a professional ethical hacker or pen tester, you should possess the required knowledge to investigate the security of cryptographic systems. In order to confirm the security of the cryptographic systems, you must implement various cryptography attacks to evade the system’s security by exploiting vulnerabilities in codes, ciphers, cryptographic protocols, or key management schemes.

- In this lab, you will learn how to compromise cryptographic systems using various cryptanalysis techniques and tools that help in breaching cryptographic security.


#### **Overview of Cryptanalysis**

- Cryptanalysis can be performed using various methods, including the following:
	- **Linear Cryptanalysis**: A known plaintext attack that uses a linear approximation to describe the behavior of the block cipher
	- **Differential Cryptanalysis**: The examination of differences in an input and how this affects the resultant difference in the output
	- **Integral Cryptanalysis**: This attack is useful against block ciphers based on substitution-permutation networks and is an extension of differential cryptanalysis


### Perform Cryptanalysis using CrypTool

- CrypTool is a freeware program that enables you to apply and analyze cryptographic mechanisms, and has the typical look and feel of a modern Windows application. CrypTool includes a multitude of state-of-the-art cryptographic functions and allows you to both learn and use cryptography within the same environment. CrypTool is a free, open-source e-learning application used in the implementation and analysis of cryptographic algorithms.
- Navigate to **\Cryptanalysis Tools\CrypTool** and double-click **SetupCrypTool_1_4_41_en.exe**.
- Click the **File** option from the menu bar and select **New** to create encrypted data.
- The **Unnamed1** notepad appears; insert some text into the file. You will be encrypting this content.
- From the menu bar, click **Encrypt/Decrypt** and navigate to **Symmetric (modern)** --> **RC2…**.
	- RC2 is a symmetric-key block cipher. It is a 64-bit block cipher with variable key size and uses 18 rounds.
- The **Key Entry: RC2** dialog box appears; keep the **Key length** set to default (**8 bits**).
- In the text field below **Key length**, enter **05** as **hexadecimal characters**, and click **Encrypt**.
	- The chosen hexadecimal character acts as a key that you must send to the intended user along with the encrypted file.
- The **RC encryption of Unnamed1** notepad file appears.
- To save, click **File** in the menu bar and select **Save**.
- Now, you can send this file to the intended person by email or any other means and provide him/her with the hex value, which will be used to decrypt the file.
- Assume that you are the intended recipient (working on Windows Server 2019) of the encrypted file through the shared network drive and the key to open the encrypted data was sent to you via an email. Using this, you can decrypt the encrypted data and see the data in plain-text.
- From the menu bar, click **Encrypt/Decrypt** and navigate to **Symmetric (modern)** **--> RC2…**
- The **Key Entry: RC2** dialog box appears; leave the **Key length** set to default (**8 bits**).
- In the text field below **Key length**, enter **05** as **hexadecimal characters**, and click **Decrypt**.
- The decrypted text appears.
- Now we can do the same using Triples DES Encryption.
- From the menu bar, click **Encrypt/Decrypt** and navigate to **Symmetric (modern) --> Triple DES (ECB)…**
- The **Key Entry: Triple DES (ECB)** dialog-box appears; leave the **Key length** set to default (**128 bits (effectively 112 bits**)).
- In the text field below **Key length**, enter the combinations of **12** as **hexadecimal characters**, and click **Encrypt**.
	- The chosen hexadecimal characters act like a key that you must send to the intended user along with the encrypted file.
- The **Triple DES (ECB) encryption of Unnamed1** notepad appears.
- To save the file, click **File** in the menu bar and select **Save**.



### Perform Cryptanalysis using AlphaPeeler

- AlphaPeeler is a powerful tool for learning cryptology. It can be useful as an instructor’s teaching aid and to create assignments for classical cryptography. You can easily learn classical techniques such as frequency analysis of alphabets, mono-alphabetic substitution, Caesar cipher, transposition cipher, Vigenere cipher, and Playfair cipher. AlphaPeeler Professional (powered by crypto++ library) also includes DES, Gzip/Gunzip, MD5, SHA-1, SHA-256, RIPEMD-16, RSA key generation, RSA crypto, RSA signature & validation, and generation of secret share files.
- Navigate to **\Cryptanalysis Tools\AlphaPeeler** and double-click **AlphaPeelerPro1.3wse.exe**.
- **AlphaPeeler Professional** initializes and the **AlphaPeeler** main window appears.
- Click **Professional Crypto** from the menu bar and select **DES crypto** from the options.
- The **DES crypto** pop-up appears; click the ellipsis icon under the **Plain text file** option.
- The **Open** window appears; navigate to **Desktop** and select **Test.txt** file; then, click **Open**.
	- Here, we are selecting the file that we will encrypt and this will act as an input file.
- In the **DES crypto** pop-up; click the ellipsis icon under the **Cipher text file** option.
- The **Open** window appears; select the save location and name the file as **Confidential.txt**; then, click **Open**.
- In the **DES crypto** pop-up; insert the password into the **Pass phrase** field and click **DES-EDE (CBC)** to encrypt the text file.
- Double-click **Confidential.txt** to open, and you can observe that the file’s content is encrypted.
- To decrypt it, AlphaPeeler** main window appears; click **File** from the menu bar and click **Open…**
- The **Open** window appears; in the **Look in** field, navigate to the location and select **Confidential.txt** file; then, click **Open**.
- The **Confidential.txt** file appears; click **Professional crypto** from the menu bar and select the **DES crypto** option.
- The **DES crypto** pop-up appears; click the ellipsis icon next to the **Plain text file** option.
- The **Open** window appears; navigate to **Desktop** and name the file **Result.txt**; then, click **Open**.
	- Here, we are creating an output file that will be in plain-text.
- 1.  In the **DES crypto** pop-up; click the ellipsis icon under the **Cipher text file** option.
- The **Open** window appears; select the encrypted file.
- In the **DES crypto** pop-up, enter the password that you provided in earlier into the **Pass phrase** field and click the **DES-EDE (CBC)** button next to **Decrypt** to decrypt the text file.
- Navigate to **Desktop** and double click the **Result.txt** file. You can observe the file content in plain-text.