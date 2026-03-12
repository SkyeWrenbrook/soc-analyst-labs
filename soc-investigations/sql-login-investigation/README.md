# sql-login-investigation

## Project Objective
Identify suspicious login activity by filtering authentication logs using SQL queries.
As part of a cybersecurity investigation, a potential security incident was identified that took place outside of normal business hours. To determine the scope of the incident, SQL queries were used to analyze login activity stored in the log_in_attempts table.
The goal was to isolate all failed login attempts occurring after 18:00, using SQL filter conditions to narrow the results. The login_time column was used to filter by time, and the success column — where a value of 0 (or FALSE) indicates a failed attempt — was used to exclude successful logins.

The resulting query and a detailed explanation of its logic were documented in the "Retrieve After Hours Failed Login Attempts" section of this document, along with screenshots of the query executed in the lab environment.

## Tools Used
- MariaDB
- SQL filtering
- Log analysis
- Query filtering (AND, OR, NOT, LIKE)

# Retrieve after hours failed login attempts
<img width="889" height="489" alt="Screenshot 2026-02-27 210206" src="https://github.com/user-attachments/assets/c155aae2-ae42-4ddd-ad03-743ca7697b00" />

# Retrieve login attempts on specific dates
To support the investigation, login activity was filtered to display attempts that occurred on 2022-05-08 and 2022-05-09. The login_date column in the log_in_attempts table was used with an OR condition to return records from either date. Using SELECT * returned all columns, providing full visibility into each login event — including user, time, location, IP address, and success status — for focused analysis of activity during the selected timeframe.
<img width="887" height="693" alt="Screenshot 2026-02-27 210257" src="https://github.com/user-attachments/assets/2e3b6f9d-de92-455a-9018-7229d6e76473" />

# Retrieve login attempts outside of Mexico
Login attempts were filtered to exclude activity originating from Mexico. A NOT LIKE condition was applied to the country column to return only records from other locations.
This query shifts focus to login activity outside the expected region, making it easier to surface unusual or potentially suspicious access patterns from external sources. 
<img width="891" height="765" alt="Screenshot 2026-02-27 210358" src="https://github.com/user-attachments/assets/f5d46443-9f79-4ae7-b02f-8acec1ef2ff2" />

# Retrieve employees in Marketing and East Region Office
To narrow the employee data, records were filtered to return only users in the Marketing department assigned to East region offices. Conditions were applied to both the department and office columns, using a LIKE filter to match East office locations. 
This isolates a specific subset of employees, making it easier to perform targeted analysis or reporting on that group. 
<img width="890" height="285" alt="Screenshot 2026-02-27 211741" src="https://github.com/user-attachments/assets/14156224-76cf-493a-980e-31c23e871b8b" />

# Retrieve employees in Finance or Sales
The employees table was filtered to return records for users in either the Finance or Sales departments. An OR condition was used to capture both departments within a single result set. 
This allows related groups to be viewed together, streamlining cross-departmental comparison and analysis. 

<img width="890" height="780" alt="Screenshot 2026-02-27 212323" src="https://github.com/user-attachments/assets/c070436c-7b35-4df5-80ad-f8e79e574a28" />

# Retrieve all employees not in IT
This query filters the employee table to display records for users who are not part of the IT department. A NOT condition was applied to the department column to exclude IT personnel from the results. 
This helps isolate non-IT employees for comparison, auditing, or targeted analysis. 

<img width="890" height="227" alt="Screenshot 2026-02-27 212513" src="https://github.com/user-attachments/assets/eb83241c-ea94-42c5-8b24-4b51f37b92af" />

# Summary
This project demonstrates the use of SQL filtering techniques to support a cybersecurity investigation and data analysis workflow. Multiple queries were applied to organizational datasets to retrieve relevant information by filtering login activity based on time, date, location, and success status, as well as narrowing employee records by department and office location. By combining conditions such as AND, OR, NOT, and LIKE, the investigation shows how SQL can be used to isolate data efficiently, identify unusual patterns, and support incident analysis and organizational reporting. 

