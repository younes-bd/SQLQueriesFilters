<h1> Apply filters to SQL queries </h1>

<h2> Description : </h2>
My organization is working to make their system more secure. It is my job to ensure the system is safe, investigate all potential security issues, and update employee computers as needed. The following steps provide examples of how I used SQL with filters to perform security-related tasks.
<br />

<h2> Languages and Utilities Used </h2>

- <b> PowerShell </b> 
- <b> Diskpart </b>

<h2>Environments Used </h2>

- <b>Windows 10</b> (21H2)

<h2>Program walk-through:</h2>

<p align="center">
Retrieve after hours failed login attempts: <br/>
 
 There was a potential security incident that occurred after business hours (after 18:00). All after hours login attempts that failed need to be investigated.<br/>
 The following code demonstrates how I created a SQL query to filter for failed login attempts that occurred after business hours.
 <br/>
 <br/>
 <img src="https://i.imgur.com/AnP99bb.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <br/>
<br/>
The first part of the screenshot is my query, and the second part is a portion of the output. This query filters for failed login attempts that occurred after 18:00. First, I started by selecting all data from the log_in_attempts table. Then, I used a WHERE clause with an AND operator to filter my results to output only login attempts that occurred after 18:00 and were unsuccessful. The first condition is login_time > '18:00', which filters for the login attempts that occurred after 18:00. The second condition is success = FALSE, which filters for the failed login attempts. 

<p align="center">
Retrieve login attempts on specific dates: <br/>
 
A suspicious event occurred on 2022-05-09. Any login activity that happened on 2022-05-09 or on the day before needs to be investigated.
The following code demonstrates how I created a SQL query to filter for login attempts that occurred on specific dates.
<br/>
<br/>
<img src="https://i.imgur.com/UqiPISx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<br/>
The first part of the screenshot is my query, and the second part is a portion of the output. This query returns all login attempts that occurred on 2022-05-09 or 2022-05-08. First, I started by selecting all data from the log_in_attempts table. Then, I used a WHERE clause with an OR operator to filter my results to output only login attempts that occurred on either 2022-05-09 or 2022-05-08. The first condition is login_date = '2022-05-09', which filters for logins on 2022-05-09. The second condition is login_date = '2022-05-08', which filters for logins on 2022-05-08.
 
<p align="center">
Retrieve login attempts outside of Mexico: <br/>
 
After investigating the organization’s data on login attempts, I believe there is an issue with the login attempts that occurred outside of Mexico. These login attempts should be investigated. <br/>
The following code demonstrates how I created a SQL query to filter for login attempts that occurred outside of Mexico:
<br/>
<br/>
<img src="https://i.imgur.com/ELRUin1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<br/>
The first part of the screenshot is my query, and the second part is a portion of the output. This query returns all login attempts that occurred in countries other than Mexico. First, I started by selecting all data from the log_in_attempts table. Then, I used a WHERE clause with NOT to filter for countries other than Mexico. I used LIKE with MEX% as the pattern to match because the dataset represents Mexico as MEX and MEXICO. The percentage sign (%) represents any number of unspecified characters when used with LIKE. 

<p align="center">
Retrieve employees in Marketing: <br/>
 
My team wants to update the computers for certain employees in the Marketing department. To do this, I have to get information on which employee machines to update.
<br/>
The following code demonstrates how I created a SQL query to filter for employee machines from employees in the Marketing department in the East building.
<br/>
 <img src="https://i.imgur.com/KDTLkdd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<br/>
The first part of the screenshot is my query, and the second part is a portion of the output. This query returns all employees in the Marketing department in the East building. First, I started by selecting all data from the employees table. Then, I used a WHERE clause with AND to filter for employees who work in the Marketing department and in the East building. I used LIKE with East% as the pattern to match because the data in the office column represents the East building with the specific office number. The first condition is the department = 'Marketing' portion, which filters for employees in the Marketing department. The second condition is the office LIKE 'East%' portion, which filters for employees in the East building.
 
<p align="center">
Retrieve employees in Finance or Sales: <br/>
 
The machines for employees in the Finance and Sales departments also need to be updated. Since a different security update is needed, I have to get information on employees only from these two departments.<br/>
The following code demonstrates how I created a SQL query to filter for employee machines from employees in the Finance or Sales departments.
<br/>
 <img src="https://i.imgur.com/bOHzPTz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <br/>
 <br/>
The first part of the screenshot is my query, and the second part is a portion of the output. This query returns all employees in the Finance and Sales departments. First, I started by selecting all data from the employees table. Then, I used a WHERE clause with OR to filter for employees who are in the Finance and Sales departments. I used the OR operator instead of AND because I want all employees who are in either department. The first condition is department = 'Finance', which filters for employees from the Finance department. The second condition is department = 'Sales', which filters for employees from the Sales department.

 <p align="center">
Retrieve all employees not in IT: <br/>
 
My team needs to make one more security update on employees who are not in the Information Technology department. To make the update, I first have to get information on these employees.<br/>
The following demonstrates how I created a SQL query to filter for employee machines from employees not in the  Information Technology department.
<br/>
 <img src="https://i.imgur.com/02gOC9n.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<br/>
The first part of the screenshot is my query, and the second part is a portion of the output. The query returns all employees not in the Information Technology department. First, I started by selecting all data from the employees table. Then, I used a WHERE clause with NOT to filter for employees not in this department.

<p align="center">
Summary: <br/>
 
I applied filters to SQL queries to get specific information on login attempts and employee machines. I used two different tables, log_in_attempts and employees. I used the AND, OR, and NOT operators to filter for the specific information needed for each task. I also used LIKE and the percentage sign (%) wildcard to filter for patterns.
<br/>
<br/>


<h1> 1. Project Title: SQL Query Filtering for Enhanced Security </h1>

<h2> Project Overview: </h2>
In this project, I addressed various security concerns within the organization's systems by leveraging SQL queries with strategic filters. The goal was to identify and investigate potential security threats and streamline the process of updating employee computers.

<h2> 1. Retrieve After-Hours Failed Login Attempts: </h2>
Objective: Investigate potential security incidents by analyzing failed login attempts after business hours.

<h3> SQL Query: </h3>

```
SELECT * FROM log_in_attempts WHERE login_time > '18:00' AND success = FALSE;
```

<h3> Outcome: </h3>
Identified and investigated after-hours failed login attempts.

<h2> 2. Retrieve Login Attempts on Specific Dates: </h2>
Objective: Investigate suspicious events on a specific date and the day before.

<h3> SQL Query: </h3>

```
SELECT * FROM log_in_attempts
WHERE login_date = '2022-05-09' OR login_date = '2022-05-08';
```

<h3> Outcome: </h3>
Retrieved login attempts on the specified dates for further investigation.

<h2> 3. Retrieve Login Attempts Outside of Mexico: </h2>
Objective: Investigate and address login attempts originating from countries other than Mexico.

<h3> SQL Query: </h3>

```
SELECT * FROM log_in_attempts
WHERE NOT country LIKE 'MEX%';
```

<h3> Outcome: </h3>
Identified and isolated login attempts outside of Mexico for additional scrutiny.

<h2> 4. Retrieve Employees in Marketing: </h2>
Objective: Gather information on employee machines in the Marketing department located in the East building.

<h3> SQL Query: </h3>

```
SELECT * FROM employees
WHERE department = 'Marketing' AND office LIKE 'East%';
```

<h3> Outcome: </h3>
Obtained a list of employees in the Marketing department in the East building for computer updates.

<h2> 5. Retrieve Employees in Finance or Sales: </h2>
Objective: Gather information on employee machines in the Finance or Sales departments.

<h3> SQL Query: </h3>

```
SELECT * FROM employees
WHERE department = 'Finance' OR department = 'Sales';
```

<h3> Outcome: </h3>
Compiled a list of employees in the Finance and Sales departments for specific security updates.

<h2> 6. Retrieve All Employees Not in IT: </h2>
Objective: Gather information on employees not in the Information Technology department for a distinct security update.

<h3> SQL Query: </h3>

```
SELECT * FROM employees
WHERE NOT department = 'Information Technology';
```

<h3> Outcome: </h3>
Identified and isolated employees not in the IT department for targeted security measures.

<h2> Summary: </h2>
I applied targeted filters to SQL queries to extract specific information related to login attempts and employee machines. The use of AND, OR, and NOT operators, along with LIKE and wildcards, allowed for precise data retrieval, enhancing the organization's overall cybersecurity posture.


Certainly! Here are a few more examples of cybersecurity-related projects that involve SQL queries and filtering:


<h1> 2. Project Title: User Privilege Analysis </h1>

<h2> Project Overview: </h2>
To strengthen user access controls, I conducted an analysis of user privileges within the organization's database. The goal was to identify and address any unnecessary or elevated permissions.

<h2> 1. Identify Superuser Accounts: </h2>
Objective: Locate accounts with superuser privileges for potential security risks.

<h3> SQL Query: </h3>

```
SELECT username, privilege_level
FROM user_accounts
WHERE privilege_level = 'superuser';
```

<h3> Outcome: </h3>
Compiled a list of accounts with superuser privileges for further review and potential privilege reduction.

<h2> 2. Unused Accounts Cleanup: </h2>
Objective: Identify and deactivate user accounts that have not been used for an extended period.

<h3> SQL Query: </h3>

```
SELECT username, last_login
FROM user_accounts
WHERE last_login < '2023-01-01';
```
<h3> Outcome: </h3>
Identified dormant accounts for deactivation, reducing the potential attack surface.


<h1> 3. Project Title: Anomaly Detection in Network Traffic </h1>

<h2> Project Overview: </h2>
Implemented SQL queries to analyze network traffic logs for anomalies, helping to identify potential security threats or irregularities.

<h2> 1. Unusual Outbound Traffic: </h2>
Objective: Identify outbound network traffic patterns that deviate from the norm.

<h3> SQL Query: </h3>

```
SELECT source_ip, destination_ip, protocol
FROM network_logs
WHERE destination_ip NOT IN (SELECT trusted_ip FROM whitelist);
```

<h3> Outcome: </h3>
Detected and investigated unusual outbound traffic, possibly indicating a compromised system.

<h2> 2. Multiple Login Attempts from Different Locations: </h2>
Objective: Identify instances of multiple login attempts from geographically distinct locations in a short timeframe.

<h3> SQL Query: </h3>

```
SELECT username, source_ip, COUNT(DISTINCT location) AS distinct_locations
FROM login_attempts
GROUP BY username, source_ip
HAVING distinct_locations > 1;
```

<h3> Outcome: </h3>
Detected suspicious login patterns for further investigation and potential account compromise.


<h1> 4.Project Title: Data Exfiltration Detection </h1>

<h2> Project Overview: </h2>
Implemented SQL queries to monitor and detect potential data exfiltration attempts from the organization's databases.

<h2> 1. Unusual Data Transfer Volume: </h2>
Objective: Identify instances where the volume of data transferred exceeds normal patterns.

<h3> SQL Query: </h3>

```
SELECT username, table_name, COUNT(*) AS records_transferred
FROM data_transfers
GROUP BY username, table_name
HAVING records_transferred > (SELECT AVG(records_transferred) * 2 FROM data_transfers);
```

<h3> Outcome: </h3>
Detected and investigated abnormal data transfer volumes for potential data exfiltration.

<h2> 2. Unencrypted Data Transfers: </h2>
Objective: Identify data transfers that occur without encryption.

<h3> SQL Query: </h3>

```
SELECT username, table_name
FROM data_transfers
WHERE encryption = 'none';
```

<h3> Outcome: </h3>
Identified instances of unencrypted data transfers for remediation and encryption implementation.




<h1> Project Title: Insider Threat Detection </h1>

<h2> Project Overview: </h2>
Implemented SQL queries to monitor user behavior and identify potential insider threats within the organization's network.

<h2> 1. Unusual File Access Patterns: </h2>
Objective: Detect patterns of unusual file access that might indicate an insider threat.

<h3> SQL Query: </h3>

```
SELECT username, file_path
FROM file_access_logs
WHERE access_time < NOW() - INTERVAL 1 DAY
GROUP BY username
HAVING COUNT(DISTINCT file_path) > 50;
```

<h3> Outcome: </h3>
Identified users with abnormally high file access activity for further investigation.

<h2> 2. Data Exfiltration Indicators: </h2>
Objective: Monitor and identify potential data exfiltration attempts.

<h3> SQL Query: </h3>

```
SELECT username, destination_ip, data_size
FROM data_transfers
WHERE data_size > (SELECT AVG(data_size) * 2 FROM data_transfers);
```

<h3> Outcome: </h3>
Detected and investigated data transfers with unusually large sizes, indicating potential data exfiltration.

<h2> Summary: </h2>
By implementing SQL queries to monitor user behavior, I successfully identified patterns indicative of insider threats. Swift action was taken to investigate and mitigate risks associated with unusual file access patterns and potential data exfiltration attempts, contributing to an enhanced insider threat detection system.


<h1> Project Title: Security Compliance Auditing  </h1>

<h2> Project Overview: </h2>
Utilized SQL queries to conduct security compliance audits and ensure adherence to industry standards.

<h2> 1. Password Policy Compliance: </h2>
Objective: Ensure compliance with the organization's password policy.

<h3> SQL Query: </h3>

```
SELECT username, last_password_change
FROM user_accounts
WHERE last_password_change < NOW() - INTERVAL 90 DAY;
```

<h3> Outcome: </h3>
Identified users whose passwords were not changed within the specified timeframe, enforcing password policy compliance.

<h2> 2. Encryption Status Assessment: </h2>
Objective: Verify the encryption status of sensitive data in the database.

<h3> SQL Query: </h3>

```
SELECT table_name, encryption_status
FROM sensitive_data_tables
WHERE encryption_status = 'not encrypted';
```

<h3> Outcome: </h3>
Ensured that sensitive data tables were encrypted, maintaining compliance with security standards.

<h2> Summary: </h2>
Through meticulous security compliance auditing using SQL queries, I verified and enforced adherence to password policies and encryption standards. This project not only ensured a more secure environment but also facilitated ongoing compliance with industry regulations.


<h1> Project Title: Phishing Email Analysis </h1>

<h2> Project Overview: </h2>
Implemented SQL queries to analyze email logs and detect potential phishing attempts.

<h1> 1. Unusual Email Sending Patterns: </h1>
Objective: Identify unusual patterns in email sending that may indicate phishing.

<h3> SQL Query: </h3>

```
SELECT sender, recipient, COUNT(*) AS email_count
FROM email_logs
GROUP BY sender, recipient
HAVING email_count > 100;
```

<h3> Outcome: </h3>
Detected instances of users sending a high volume of emails to different recipients for investigation.

<h2> 2. Malicious Attachment Detection: </h2>
Objective: Identify emails with potentially malicious attachments.

<h3> SQL Query: </h3>

```
SELECT sender, subject, attachment_name
FROM email_logs
WHERE attachment_type = 'executable';
```

<h3> Outcome: </h3>
Detected and investigated emails with attachments of executable file types, potentially indicating malicious activity.

<h2> Summary: </h2>
This project significantly contributed to the organization's cybersecurity by analyzing email logs for potential phishing threats. Identification of unusual email sending patterns and detection of emails with suspicious attachments allowed for prompt investigation and mitigation of potential phishing attempts, thereby enhancing email security.


<h1> Project Title: Network Anomaly Detection </h1>

<h2> Project Overview: </h2>
Implemented SQL queries to monitor network traffic and detect anomalies indicative of security breaches.

<h2> 1. Unusual Protocol Usage: </h2>
Objective: Identify instances of uncommon network protocols being used.

<h3> SQL Query: </h3>

```
SELECT source_ip, destination_ip, protocol
FROM network_traffic
WHERE protocol NOT IN ('HTTP', 'HTTPS', 'TCP', 'UDP');
```

<h3> Outcome: </h3>
Detected and investigated instances of non-standard protocols, potentially indicating malicious activity.

<h2> 2. High Volume Outbound Connections: </h2>
Objective: Monitor for high volumes of outbound connections from a single source.

<h3> SQL Query: </h3>

```
SELECT source_ip, COUNT(destination_ip) AS connection_count
FROM network_traffic
GROUP BY source_ip
HAVING connection_count > 1000;
```

<h3> Outcome: </h3>
Identified and investigated sources generating an unusually high volume of outbound connections.

<h2> Summary: </h2>
By leveraging SQL queries to analyze network traffic, I successfully detected and investigated anomalies in protocol usage and outbound connections. This proactive approach to network anomaly detection contributed to early threat identification and mitigation.

<h1> Project Title: Cloud Security Assessment </h1>

<h2> Project Overview: </h2>
Conducted a security assessment of the organization's cloud infrastructure using SQL queries.

<h2> 1. Unauthorized Access to Cloud Resources: </h2>
Objective: Identify instances of unauthorized access to cloud resources.

<h3> SQL Query: </h3>

```
SELECT username, resource_name
FROM cloud_access_logs
WHERE access_status = 'unauthorized';
```
<h3> Outcome: </h3>
Detected and investigated instances of unauthorized access to cloud resources.

<h2> 2. Insecurely Configured Buckets: </h2>
Objective: Identify cloud storage buckets with insecure configurations.

<h3> SQL Query: </h3>

```
SELECT bucket_name, public_access
FROM cloud_storage_buckets
WHERE public_access = 'true';
```

<h3> Outcome: </h3>
Identified and secured cloud storage buckets with unintentional public access.

<h2> Summary: </h2>
This project focused on assessing and enhancing the security of the organization's cloud infrastructure. By identifying and addressing unauthorized access and insecurely configured resources, I contributed to bolstering the overall security posture of the cloud environment.

<h1> Project Title: Mobile Device Security Analysis </h1>

<h2> Project Overview: </h2>
Used SQL queries to assess the security of mobile devices connected to the organization's network.

<h2> 1. Unauthorized Devices: </h2>
Objective: Identify mobile devices not authorized to connect to the corporate network.

<h3> SQL Query: </h3>

```
SELECT device_name, device_type
FROM mobile_devices
WHERE authorized = 'false';
```

<h3> Outcome: </h3>
Detected unauthorized mobile devices connected to the corporate network.

<h2> 2. Outdated Operating Systems: </h2>
Objective: Identify mobile devices with outdated operating systems.

<h3> SQL Query: </h3>

```
SELECT device_name, operating_system_version
FROM mobile_devices
WHERE operating_system_version < 'latest_version';
```

<h3> Outcome: </h3>
Identified devices with outdated operating systems for timely updates.

<h2> Summary: </h2>
By leveraging SQL queries to analyze mobile device data, I successfully identified and addressed security risks. Detection of unauthorized devices and devices with outdated operating systems contributed to a more secure mobile device environment.


<h1> Project 4: Insider Threat Detection Enhancement </h1>

<h2> Project Overview: </h2>
Implemented advanced SQL queries to enhance the organization's capability to detect and respond to insider threats.

<h2> 1. Behavior Anomalies: </h2>
Objective: Identify abnormal user behavior patterns that may indicate an insider threat.

<h2> SQL Query: </h2>

```
SELECT username, activity_type, COUNT(*) AS activity_count
FROM user_activity_logs
GROUP BY username, activity_type
HAVING activity_count > 100;\
```

<h2> Outcome: </h2>
Detected and investigated users exhibiting abnormal patterns of activity for potential insider threats.

<h2> 2. Data Exfiltration Patterns: </h2>
Objective: Monitor data access and identify patterns indicative of potential data exfiltration.

<h3> SQL Query: </h3>

```
SELECT username, destination_ip, data_size
FROM data_transfers
WHERE data_size > (SELECT AVG(data_size) * 2 FROM data_transfers);
```

<h3> Outcome: </h3>
Identified and investigated instances of data transfers with unusually large sizes, suggesting potential data exfiltration.

<h2> Summary: </h2>
By applying advanced SQL queries, I significantly improved the organization's ability to detect insider threats. The identification of abnormal behavior and potential data exfiltration patterns provided valuable insights for swift response and mitigation.

<h1> Project 5: Endpoint Security Analysis </h1>

<h2> Project Overview: </h2>
Utilized SQL queries to analyze endpoint security logs and strengthen the organization's overall security posture.

<h2> 1. Malware Detection: </h2>
Objective: Identify systems with signs of potential malware infections.

<h3> SQL Query: </h3>

```
SELECT system_name, malware_signature
FROM endpoint_security_logs
WHERE detection_status = 'infected';
```

<h3> Outcome: </h3>
Detected and isolated systems with indications of malware infections for further analysis and remediation.

<h2> 2. Unusual Application Activity: </h2>
Objective: Monitor for unusual activity related to applications on endpoints.

<h3> SQL Query: </h3>

```
SELECT system_name, application_name, activity_type
FROM endpoint_activity_logs
WHERE activity_type = 'unusual';
```

<h3> Outcome: </h3>
Identified and investigated endpoints exhibiting unusual application-related activities.

<h3> Summary: </h3>
This project focused on enhancing endpoint security through SQL query analysis. The identification of malware infections and unusual application activities allowed for prompt responses, improving the overall resilience of endpoint security.


<h1> Project 6: Security Awareness Training Evaluation </h1>

<h2> Project Overview: </h2>
Utilized SQL queries to assess the effectiveness of the organization's security awareness training program.

<h2> 1. Phishing Simulation Results: </h2>
Objective: Analyze results from simulated phishing exercises to evaluate user awareness.

<h3> SQL Query: </h3>

```
SELECT username, clicked_links
FROM phishing_simulation_results
WHERE clicked_links > 0;
```

<h3> Outcome: </h3>
Analyzed data on users who clicked on simulated phishing links to identify areas for improvement in security awareness training.

<h2> 2. Password Hygiene: </h2>
Objective: Evaluate improvements in password hygiene post-training.

<h3> SQL Query: </h3>

```
SELECT username, last_password_change
FROM user_accounts
WHERE last_password_change >= '2023-01-01';
```

<h3> Outcome: </h3>
Reviewed changes in password update behaviors to assess the impact of security awareness training.

<h2> Summary: </h2>
Through the analysis of simulated exercises and real-world data, this project assessed the impact of security awareness training. Identification of areas needing improvement and positive changes in password hygiene demonstrated the effectiveness of the training program.






 
<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
