# Apply-appropriate-filters-to-refine-the-SQL-queries.

## Objective

To support my organization’s security improvements, I oversee system protection, examine possible vulnerabilities, and update employee computers. The following examples show how I used SQL with filters to carry out these security tasks.

### Skills Learned

  - How to use the `LIKE` operator to search for patterns.
  - Details on applying date and time filters in SQL.
  - Details on combining conditions with AND and OR in SQL filters.
  - Overview of applying the NOT operator in SQL filters.

### Tools Used

- LINUX(Bash shell)
- MariaDB 

## Steps
  1. Retrieve failed login attempts that occurred after business hours:
    A potential security incident took place outside of business hours (after 18:00). All failed login attempts during this time need to be investigated. The SQL query below demonstrates how I filtered for failed login attempts that occurred after business hours.

<img src="https://i.imgur.com/6Br5Ct5.png" alt="Image description">
<img src="https://i.imgur.com/1RgtSIV.png" alt="Image description">

The first part of the screenshot shows my SQL query, and the second part displays a portion of the output. This query filters failed login attempts that occurred after 18:00. I began by selecting all data from the `log_in_attempts` table. Then, I applied a `WHERE` clause using the `AND` operator to refine the results to only include unsuccessful login attempts made after 18:00.

The first condition, `login_time > '18:00'`, filters for login attempts that occurred after business hours. The second condition, `success = FALSE`, ensures that only failed login attempts are returned.

  2. Query login attempts that took place on particular dates:
    A suspicious event was detected on 2022-05-09. Therefore, all login activity that took place on that date, as well as the previous day, must be investigated.
  The SQL query below demonstrates how I filtered login attempts that occurred on these specific dates.

<img src="https://i.imgur.com/eeboa4V.png" alt="Image description">
<img src="https://i.imgur.com/mDNEyli.png" alt="Image description">

The first part of the screenshot shows my SQL query, and the second part displays a portion of the output. This query retrieves all login attempts that took place on either 2022-05-09 or 2022-05-08. I began by selecting all data from the `log_in_attempts` table. Then, I applied a `WHERE` clause with an `OR` operator to filter the results to only include login attempts that occurred on those two dates.

The first condition, `login_date = '2022-05-09'`, filters for logins on May 9, 2022. The second condition, `login_date = '2022-05-08'`, filters for logins from the previous day, May 8, 2022.

  3. Extract login attempts originating from locations outside of Mexico:
     After analyzing the organization’s login attempt data, I identified potential concerns with login activity originating from outside of Mexico. These attempts require further investigation.
The SQL query below demonstrates how I filtered for login attempts that occurred outside of Mexico.

<img src="https://i.imgur.com/GEE25Qf.png" alt="Image description">
<img src="https://i.imgur.com/mkDNylM.png" alt="Image description">

The first part of the screenshot shows my SQL query, and the second part displays a portion of the output. This query retrieves all login attempts that originated from countries other than Mexico. I began by selecting all data from the `log_in_attempts` table. Then, I applied a `WHERE` clause with the `NOT` operator to exclude entries from Mexico.

To account for variations in how Mexico is represented in the dataset—such as `MEX` and `MEXICO`—I used the `LIKE 'MEX%'` pattern. The percentage symbol (%) acts as a wildcard that represents any number of unspecified characters, making it possible to match both values.

  4. Extract a list of employees who work in Marketing:
     My team needs to update the computers for specific employees in the Marketing department. To proceed, I first need to identify which employee machines require updates.
The SQL query below demonstrates how I filtered for employee machines belonging to Marketing department employees located in the East building.

<img src="https://i.imgur.com/FX1tMvA.png" alt="Image description">

The first part of the screenshot shows my SQL query, and the second part displays a portion of the output. This query retrieves all employees who work in the Marketing department and are located in the East building. I began by selecting all data from the `employees` table. Then, I applied a `WHERE` clause using the `AND` operator to filter the results to include only employees in the Marketing department and assigned to the East building.

I used `LIKE 'East%'` to match values in the `office` column because the office information contains the building name followed by a specific office number.
The first condition, `department = 'Marketing'`, filters for employees who belong to the Marketing department.
The second condition, `office LIKE 'East%'`, filters for employees working in the East building.

  5. Obtain employee data for those in the Finance or Sales departments:
      Employee machines in the Finance and Sales departments also require updates. Since these departments need a different security update, I must gather information specifically for employees in these two groups.
The SQL query below demonstrates how I filtered for employee machines belonging to employees in either the Finance or Sales departments.

<img src="https://i.imgur.com/6vYGrWJ.png" alt="Image description">
<img src="https://i.imgur.com/Pz0ltzs.png" alt="Image description">

The first part of the screenshot shows my SQL query, and the second part displays a portion of the output. This query retrieves all employees who work in the Finance or Sales departments. I began by selecting all data from the `employees` table. Then, I applied a `WHERE` clause using the `OR` operator to return employees who belong to either department.

I used `OR` instead of `AND` because I wanted to include employees from either the Finance or Sales department.
The first condition, `department = 'Finance'`, filters for employees in the Finance department.
The second condition, `department = 'Sales'`, filters for employees in the Sales department.

  6. Filter and return employees not belonging to the IT department:
    My team needs to apply an additional security update to employees who are not part of the Information Technology department. To proceed, I first need to gather information on these employees.
The following SQL query demonstrates how I filtered for employee machines belonging to employees outside of the Information Technology department.

<img src="https://i.imgur.com/cfHGnPZ.png" alt="Image description">
<img src="https://i.imgur.com/NrM8YjF.png" alt="Image description">

The first part of the screenshot shows my SQL query, and the second part displays a portion of the output. This query retrieves all employees who are not in the Information Technology department. I began by selecting all data from the `employees` table, and then applied a `WHERE` clause using the `NOT` operator to exclude employees from that department.

SUMMARY
       I applied filters to SQL queries to extract specific information related to login attempts and employee machines. This involved using data from two different tables: `log_in_attempts` and `employees`. To refine the results, I utilized the `AND`, `OR`, and `NOT` operators to meet the requirements of each task. Additionally, I used the `LIKE` operator along with the `%` wildcard to filter data based on patterns.

