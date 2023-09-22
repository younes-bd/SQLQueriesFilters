<h1> Apply filters to SQL queries </h1>

<h2>Description</h2>
My organization is working to make their system more secure. It is my job to ensure the system is safe, investigate all potential security issues, and update employee computers as needed. The following steps provide examples of how I used SQL with filters to perform security-related tasks.
<br />

<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>Diskpart</b>

<h2>Environments Used </h2>

- <b>Windows 10</b> (21H2)

<h2>Program walk-through:</h2>

<p align="center">
Retrieve after hours failed login attempts: <br/>
 
 There was a potential security incident that occurred after business hours (after 18:00). All after hours login attempts that failed need to be investigated.
 The following code demonstrates how I created a SQL query to filter for failed login attempts that occurred after business hours.
 <br/>
 <br/>
 <img src="https://i.imgur.com/AnP99bb.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
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
The first part of the screenshot is my query, and the second part is a portion of the output. This query returns all login attempts that occurred on 2022-05-09 or 2022-05-08. First, I started by selecting all data from the log_in_attempts table. Then, I used a WHERE clause with an OR operator to filter my results to output only login attempts that occurred on either 2022-05-09 or 2022-05-08. The first condition is login_date = '2022-05-09', which filters for logins on 2022-05-09. The second condition is login_date = '2022-05-08', which filters for logins on 2022-05-08.
 
<p align="center">
Retrieve login attempts outside of Mexico: <br/>
 
After investigating the organization’s data on login attempts, I believe there is an issue with the login attempts that occurred outside of Mexico. These login attempts should be investigated. <br/>
The following code demonstrates how I created a SQL query to filter for login attempts that occurred outside of Mexico:
<br/>
<br/>
<img src="https://i.imgur.com/ELRUin1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
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
The first part of the screenshot is my query, and the second part is a portion of the output. This query returns all employees in the Marketing department in the East building. First, I started by selecting all data from the employees table. Then, I used a WHERE clause with AND to filter for employees who work in the Marketing department and in the East building. I used LIKE with East% as the pattern to match because the data in the office column represents the East building with the specific office number. The first condition is the department = 'Marketing' portion, which filters for employees in the Marketing department. The second condition is the office LIKE 'East%' portion, which filters for employees in the East building.
 
<p align="center">
Retrieve employees in Finance or Sales: <br/>
 
The machines for employees in the Finance and Sales departments also need to be updated. Since a different security update is needed, I have to get information on employees only from these two departments.<br/>
The following code demonstrates how I created a SQL query to filter for employee machines from employees in the Finance or Sales departments.
<br/>
 <img src="https://i.imgur.com/bOHzPTz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <br/>
The first part of the screenshot is my query, and the second part is a portion of the output. This query returns all employees in the Finance and Sales departments. First, I started by selecting all data from the employees table. Then, I used a WHERE clause with OR to filter for employees who are in the Finance and Sales departments. I used the OR operator instead of AND because I want all employees who are in either department. The first condition is department = 'Finance', which filters for employees from the Finance department. The second condition is department = 'Sales', which filters for employees from the Sales department.
 
<p align="center">
Summary: <br/>
 
I changed multiple permissions to match the level of authorization my organization wanted for files and directories in the projects directory. The first step in this was using ls -la to check the permissions for the directory. This informed my decisions in the following steps. I then used the chmod command multiple times to change the permissions on files and directories.
 <br/>
 <br/>

 
<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
