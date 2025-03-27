# How to use Nessus?

- What is Nessus?
- Installation and Initial Configuration
- Creating a Scan Profile
- Analysis of Scan Results
- Reporting and Exporting
- Important

### What is Nessus?
- Nessus is a vulnerability scanning tool developed by Tenable.
- It is used to detect security vulnerabilities in systems.
- It has a large vulnerability database and is constantly updated.

### Installation and Initial Configuration
- Nessus is downloaded from the Tenable website and the installation is complete.
  - https://www.tenable.com/downloads?loginAttempted=true

- After installation, the first configuration is made via the browser (https://localhost:8834).
- The user is created and the license key is entered.

### Create a Scan Profile

![Screenshot 2025-03-27 133121](https://github.com/user-attachments/assets/e552b139-4e10-408e-a5f2-20529e7a7467)

© Tenable Inc.

- 'New Scan' is selected to create a new scan.

![Screenshot 2025-03-27 133531](https://github.com/user-attachments/assets/823c0255-8b85-4bbd-bec6-f1c9a69c2090)

© Tenable Inc.

The main types of scans in Nessus and their brief descriptions:
1.	Basic Network Scan: Performs a general scan to detect common vulnerabilities in the network.
2.	Advanced Scan: Provides more in-depth and targeted scanning with customizable options.
3.	Web Application Tests: Applies OWASP-based checks to detect vulnerabilities in web applications.
4.	Credentialed Patch Audit: Detects missing patches and vulnerabilities by accessing the system with user information.
5.	Malware Scan: Scans the system for known malware and threats.
6.	Compliance Audit: Performs compliance audits against certain standards (PCI-DSS, HIPAA, etc.).
7.	Host Discovery: Identifies active devices and services on the network; used for discovery purposes.
8.	Mobile Device Scan: Scans for security vulnerabilities specific to mobile devices.
- From here we select the type of scan we need. Since Advanced Scan scans in detail, Advanced Scan also has settings that can be encountered in other types of scans. That's why we're going to continue with Advanced Scan.

![Screenshot 2025-03-27 133849](https://github.com/user-attachments/assets/db98e0d9-dd9e-4f65-a42f-17175b7945fb)

© Tenable Inc.

- Here the name, description and Destination of our scan are determined. We can enter the destination manually, we can export it as a file with the "Add File" option.

![Screenshot 2025-03-27 134022](https://github.com/user-attachments/assets/385391c0-e622-4cd8-a72e-2f6d35e59715)

© Tenable Inc.

The Shedule option is Disabled by default.

![Screenshot 2025-03-27 134036](https://github.com/user-attachments/assets/6ea5ee7c-9bcc-4e95-b16b-2c1c5629375a)

© Tenable Inc.

If we make it enabled, we can determine from which day and time and how often the scan we will create will run.

![Screenshot 2025-03-27 134158](https://github.com/user-attachments/assets/ce649a15-3a98-4d8d-afcd-78fbdf61a5d0)

© Tenable Inc.

In Nessus, in the "Port Scan Range" section, you specify the ports you want to scan. Here are some examples you can write:
•	All ports:
"1-65535" or "all"
•	Frequently used ports (default):
default (Nessus' default list, usually covering the 1000 most common ports)
•	A specific port range:
Example: 20-25 (Scans ports in this range)
•	Specific ports:
Example: 22,80,443 (Scans only these ports)
•	Mixed use:
Example: 20-25,80,443,8080 (Both range and specific ports)
Note: If you want to limit network traffic, it is recommended that you specify only the ports you need.

![Screenshot 2025-03-27 134347](https://github.com/user-attachments/assets/1e0a9d3d-3c16-4539-a023-0891fd8a4734)

© Tenable Inc.

The differences between TCP Scan and SYN Scan in Nessus  are as follows:
1. TCP Scan (Full TCP Connect Scan):
•	Establishes a full TCP connection to the destination port ( 3-way handshake).
•	It is more reliable because it verifies that the connection has actually been established.
•	It works slower and is more easily detected (falls into logs).
•	It is generally preferred in scans that work with user rights (non-root).
2. SYN Scan (Half-Open Scan):
•	It sends only the first step of the connection (SYN packet); It does not establish a full connection.
•	The response from the destination indicates whether the port is open or not (if it receives SYN-ACK, the port is open).
•	It's faster and more discreet; It is more difficult to detect by IDS/IPS systems.
Conclusion: SYN Scan is a faster and stealthier method, while TCP Scan is more visible but more reliable.

![Screenshot 2025-03-27 134625](https://github.com/user-attachments/assets/cfee883e-d69a-43c9-a18b-7e6e6a22f752)

 © Tenable Inc.
 
"Credentiales" allow scanning by accessing the target system with login credentials (username and password).
 What does it do?
•	By looking at the system from the inside, it detects missing patches, misconfigurations, and vulnerabilities in greater depth.
•	Accurately determines whether there is a vulnerability (false positive rate decreases).
•	It is mainly used for patch management and vulnerability verification.
You must use accounts  with the correct permissions (for example, admin/root privileges).
 A credentialed scan is a type of scan that looks at the system from the inside, not from the outside; This results in more precise and comprehensive results.

![Screenshot 2025-03-27 134815](https://github.com/user-attachments/assets/8b2edf64-8515-49d9-80da-2b991a13bbb3)

© Tenable Inc.

For Linux / Unix: When we click on the "SSH" option, we select the Authentication method section according to the Credentials information we have in the section that opens on the right. If we have Username and Password, select the Password option as the Authentication method and enter the Username and Password information. 

![Screenshot 2025-03-27 134845](https://github.com/user-attachments/assets/1e22f7ee-c15b-4c4b-bbc4-0bee3fc2eabc)

 © Tenable Inc.
 
For Windows: According to the Credentials information we have, we make a selection in the Authentication method section. If we have Username and Password, select the Password option as the Authentication method and enter the Username and Password information. 

![Screenshot 2025-03-27 135028](https://github.com/user-attachments/assets/9a0c08e5-b257-4f4e-ac8f-36565e301467)

© Tenable Inc.

"Plugins" in Nessus are modules used to detect security vulnerabilities, configuration errors, malware, and compatibility issues. Plugins are the knowledge base that determines what Nessus "looks for"; The scope and quality of the scan depend on the plugins.
What does it do?
•	Each plugin tests for a specific vulnerability or control (e.g. a CVE, a service vulnerability, or a configuration problem).
•	Plugins determine which tests will be performed in the Nessus scan.
•	Plugins are constantly updated; It is important in detecting new threats.
How to use?
•	Before you start browsing,  you can choose which categories will be active from the "Plugins" tab.
•	For example: There are titles such as "Windows", "Web Servers", "Malware", "Compliance".
•	You can enable or disable the plugins you want.

![Screenshot 2025-03-27 135218](https://github.com/user-attachments/assets/ffd39104-db24-45cf-81ec-34ac70d2f31b)

© Tenable Inc.

After making all our adjustments, we press the Save button at the bottom left and save.

Analysis of Scan Results
- When the scan is complete, vulnerabilities are sorted according to critical level.
- Description, CVE code and solution suggestion can be displayed for each vulnerability.
- Detailed analysis can be made according to filters.

Reporting and Exporting
- Scan results can be exported in PDF, HTML, or CSV format.
- Reports can be customized to present to management.
- Automatic report sending feature is also available.

Important
- Get permission from target systems before scanning.
- Plan the scan schedule carefully.
- Archive and track reports regularly.
- Keep Nessus and its add-ons up to date.

### Note: 
This content has been prepared for educational purposes to explain the usage steps of Nessus. All screenshots and software are the property of Tenable Inc. This page is not intended for commercial use.
