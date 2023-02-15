- Enumeration tools are used to collect detailed information about target systems to exploit them. Information collected by S3 enumeration tools consists of a list of misconfigured S3 buckets that are available publicly. Attackers can exploit these buckets to gain unauthorized access to them. Moreover, they can modify, delete, and exfiltrate the bucket content.


### Enumerate S3 Buckets using lazys3

- lazys3 is a Ruby script tool that is used to brute-force AWS S3 buckets using different permutations. This tool obtains the publicly accessible S3 buckets and also allows you to search the S3 buckets of a specific company by entering the company name.
- Open Terminal
	> sudo su
	> cd
	> cd lazys3
	> ls
	
	> ruby lazys3.rb (script to find the public S3 buckets)
	
	- **You can search the S3 buckets of specific company.** To do so
	> ruby lazys3.rb #companyname



### Enumerate S3 Buckets using S3Scanner
- S3Scanner is a tool that finds the open S3 buckets and dumps their contents. It takes a list of bucket names to check as its input. The S3 buckets that are found are output to a file. The tool also dumps or lists the contents of “open” buckets locally.
- Open Terminal
	> sudo su
	> cd
	> cd S3Scanner
	> pip3 install -r requirements.txt (to install required dependencies)
	> python3 ./s3scanner.py sites.txt (to run the tool)
	- Here, **sites.txt** is a text file containing the target website URL that is scanned for open S3 buckets. You can edit the **sites.txt** file to enter the target website URL of your choice.
	- You might encounter the following error: “AWS credentials not configured.” Ignore the error, as we will install and configure the AWS CLI in the next lab.

	> python3 ./s3scanner.py --include-closed --out-file found.txt --dump names.txt (to Dump all open buckets and log both open and closed buckets in found.txt)
	
	> python3 ./s3scanner.py bucket.txt (Just log open buckets in the default output file (buckets.txt)
	
	> python3 ./s3scanner.py --list names.txt (Save the file listings of all open buckets to a file)