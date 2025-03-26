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

![image](https://github.com/user-attachments/assets/012f14aa-453f-4a2b-969b-e78580a49942)

© Tenable Inc.

- 'New Scan' is selected to create a new scan.

![image](https://github.com/user-attachments/assets/e7d69cd8-d6ab-4bb7-baa2-c9c8d549663c)

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

![image](https://github.com/user-attachments/assets/af07ff9b-7d80-4e71-b9bc-730f58025d69)

© Tenable Inc.

- Here the name, description and Destination of our scan are determined. We can enter the destination manually, we can export it as a file with the "Add File" option.

![image](https://github.com/user-attachments/assets/85f8b69d-55e7-463c-8bfa-2238d4cf5b75)

© Tenable Inc.

The Shedule option is Disabled by default.

![image](https://github.com/user-attachments/assets/e03a4dd4-4081-4ea1-bd52-eb4767db2dd5)

© Tenable Inc.

If we make it enabled, we can determine from which day and time and how often the scan we will create will run.

![image](https://github.com/user-attachments/assets/260fcfbf-a132-4404-8ba6-8660a992dcd7)

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

![image](https://github.com/user-attachments/assets/5ed00cb4-aef3-4930-9c12-0c276ee78c08)

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

![image](https://github.com/user-attachments/assets/e59d3c8a-569e-44ea-a572-76675b02fb4c)

 © Tenable Inc.
 
"Credentiales" allow scanning by accessing the target system with login credentials (username and password).
 What does it do?
•	By looking at the system from the inside, it detects missing patches, misconfigurations, and vulnerabilities in greater depth.
•	Accurately determines whether there is a vulnerability (false positive rate decreases).
•	It is mainly used for patch management and vulnerability verification.
You must use accounts  with the correct permissions (for example, admin/root privileges).
 A credentialed scan is a type of scan that looks at the system from the inside, not from the outside; This results in more precise and comprehensive results.

 ![image](https://github.com/user-attachments/assets/628da0f1-cf8e-4423-9d4c-a95210c8505c)

© Tenable Inc.

For Linux / Unix: When we click on the "SSH" option, we select the Authentication method section according to the Credentials information we have in the section that opens on the right. If we have Username and Password, select the Password option as the Authentication method and enter the Username and Password information. 

![image](https://github.com/user-attachments/assets/a4cfff81-e656-47f4-bb3f-86b2db52324c)

 © Tenable Inc.
 
For Windows: According to the Credentials information we have, we make a selection in the Authentication method section. If we have Username and Password, select the Password option as the Authentication method and enter the Username and Password information. 

![image](https://github.com/user-attachments/assets/b4ea4bcc-fe02-4f40-9750-edf9bed4a564)

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

![image](https://github.com/user-attachments/assets/bd43deb1-992d-4faa-acb7-5b259c961207)

© Tenable Inc.

After making all our adjustments, we press the Save button at the bottom left and save.
Analysis of Scan Results
•	- When the scan is complete, vulnerabilities are sorted according to critical level.
•	- Description, CVE code and solution suggestion can be displayed for each vulnerability.
•	- Detailed analysis can be made according to filters.
Reporting and Exporting
•	- Scan results can be exported in PDF, HTML, or CSV format.
•	- Reports can be customized to present to management.
•	- Automatic report sending feature is also available.
Important
•	- Get permission from target systems before scanning.
•	- Plan the scan schedule carefully.
•	- Archive and track reports regularly.
•	- Keep Nessus and its add-ons up to date.

### Note: 
This content has been prepared for educational purposes to explain the usage steps of Nessus. All screenshots and software are the property of Tenable Inc. This page is not intended for commercial use.
