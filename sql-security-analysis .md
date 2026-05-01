# Applying SQL Filters for Security Investigations

**Author:** Yeasin Arafat Riyad  
**Date:** May 2026  
**Role:** Security Professional

---

## Project Description

As a security professional, I performed a series of SQL queries to investigate potential security incidents involving login attempts and employee machines. The objective was to filter large datasets—specifically the `employees` and `log_in_attempts` tables—to identify failed logins after business hours, suspicious activity from specific regions, and to locate specific employee machines for security updates. By applying filters like `AND`, `OR`, `NOT`, and `LIKE`, I was able to isolate relevant data to support the organization's security posture.

---

## SQL Queries and Analysis

### 1. Retrieve After-Hours Failed Login Attempts

**Scenario:** Investigate a potential security incident that occurred after business hours by identifying failed login attempts after 18:00 (6:00 PM).

**SQL Query:**
```sql
SELECT *
FROM log_in_attempts
WHERE login_time > '18:00' AND success = 0;
```

**Description:**  
This query uses the `WHERE` clause with the `AND` operator to filter for two specific conditions. First, `login_time > '18:00'` isolates attempts that happened after 6:00 PM. Second, `success = 0` (which can also be written as `FALSE`) identifies only the attempts that were unsuccessful. Combining these ensures the results only show high-risk, after-hours failed logins.

---

### 2. Retrieve Login Attempts on Specific Dates

**Scenario:** A suspicious event occurred on 2022-05-09. Review login attempts from that day and the day before to identify patterns.

**SQL Query:**
```sql
SELECT *
FROM log_in_attempts
WHERE login_date = '2022-05-08' OR login_date = '2022-05-09';
```

**Description:**  
The `OR` operator is used here to include records that match either of the two dates provided. By filtering the `login_date` column, I can review the login activity across both May 8th and May 9th, 2022, to identify any patterns leading up to the suspicious event.

---

### 3. Retrieve Login Attempts Outside of Mexico

**Scenario:** The security team determined that suspicious activity did not originate from Mexico. Filter out all login attempts from that country.

**SQL Query:**
```sql
SELECT *
FROM log_in_attempts
WHERE country NOT LIKE 'MEX%';
```

**Description:**  
Since Mexico is represented in the data as both "MEX" and "MEXICO," I used the `NOT LIKE` operator combined with the percent sign (`%`) wildcard. The pattern `'MEX%'` catches any string starting with "MEX," which includes both variations. Applying `NOT` excludes these records, effectively showing all login attempts originating from any country other than Mexico.

---

### 4. Retrieve Employees in Marketing and East Building

**Scenario:** Perform security updates on machines belonging to the Marketing department located specifically in the East building.

**SQL Query:**
```sql
SELECT *
FROM employees
WHERE department = 'Marketing' AND office LIKE 'East%';
```

**Description:**  
This query filters the `employees` table using `AND` to satisfy two requirements. It looks for "Marketing" in the `department` column and uses `LIKE 'East%'` on the `office` column. The `%` wildcard ensures that any office located in the East building (e.g., East-170, East-320) is included in the results.

---

### 5. Retrieve Employees in Finance or Sales

**Scenario:** A different security update is required for all employees in either the Sales or Finance departments.

**SQL Query:**
```sql
SELECT *
FROM employees
WHERE department = 'Sales' OR department = 'Finance';
```

**Description:**  
I used the `OR` operator to retrieve employees who work in either "Sales" or "Finance." This allows the query to return a consolidated list of personnel from both departments who require the machine update.

---

### 6. Retrieve All Employees Not in IT

**Scenario:** The Information Technology department had already received a specific update. Identify all other employees who still require it.

**SQL Query:**
```sql
SELECT *
FROM employees
WHERE department != 'Information Technology';
```

**Description:**  
In this query, I used the "not equal to" operator (`!=`) to filter the `department` column. This excludes everyone in the Information Technology department, providing a list of all other employees across the organization who still need the security update. This could also be written using `NOT department = 'Information Technology'`.

---

## Summary

In this activity, I utilized SQL to perform targeted data retrieval for various security scenarios. I applied filters to isolate specific timeframes, dates, and geographic locations using operators such as `AND`, `OR`, and `NOT`. Additionally, I used the `LIKE` keyword and wildcards to search for patterns within strings, such as building names and country codes. These techniques are essential for a security professional to efficiently investigate incidents, analyze login patterns, and manage organizational assets.

### Key Skills Demonstrated:
- Filtering data with `WHERE` clause
- Combining conditions using `AND` and `OR` operators
- Excluding data with `NOT` operator
- Pattern matching with `LIKE` and wildcards (`%`)
- Working with date and time data
- Analyzing security logs for incident investigation

---

## Tools Used
- **SQL** - Structured Query Language for database queries
- **Database Tables** - `log_in_attempts` and `employees`

---

*This project was completed as part of cybersecurity training to demonstrate proficiency in SQL for security analysis and incident investigation.*

---

## About the Author

**Yeasin Arafat Riyad**  
Security Professional | Cybersecurity Enthusiast

📧 Contact: a.yeasin291@gmail.com  
🐙 GitHub: github.com/Riyad291
