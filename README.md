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
Change file permissions on a hidden file: <br/>
 
The research team at my organization recently archived project_x.txt. They do not want anyone to have write access to this project, but the user and group should have read access. <br/>
The following code demonstrates how I used Linux commands to change the permissions:
<br/>
<br/>
 <img src="https://i.imgur.com/EPXXLNY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
The first two lines of the screenshot display the commands I entered, and the other lines display the output of the second command. I know .project_x.txt is a hidden file because it starts with a period (.). In this example, I removed write permissions from the user and group, and added read permissions to the group. I removed write permissions from the user with u-w. Then, I removed write permissions from the group with g-w, and added read permissions to the group with g+r. 
 
<p align="center">
Change directory permissions: <br/>
 
My organization only wants the researcher2 user to have access to the drafts directory and its contents. This means that no one other than researcher2 should have execute permissions.<br/>
The following code demonstrates how I used Linux commands to change the permissions:
<br/>
<br/>
 <img src="https://i.imgur.com/xdJrvGr.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 
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
