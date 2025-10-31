# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
--
-- How many appointments are scheduled for each patient?

-- SELECT PatientID , count(AppointmentID) as TotalAppointments
FROM Appointments 
group by PatientID
ORDER BY PatientID
```

**Output:**
<img width="693" height="635" alt="451344482-c6fc55d9-d0f2-4bd5-9f37-031bfaa8a064" src="https://github.com/user-attachments/assets/8716500c-708e-43b9-b24f-62f02fb3e76b" />



**Question 2**
---
-- What is the average duration of insurance coverage for patients covered by each insurance company?

-- SELECT InsuranceCompany, AVG(enddate - startdate) AS AvgCoverageDurationDays
FROM Insurance
GROUP BY InsuranceCompany;
```

**Output:**
<img width="955" height="684" alt="451344813-146996dc-b11b-4d32-a416-1363b749fc70" src="https://github.com/user-attachments/assets/5754bd6f-2ab1-4342-a13b-769fed80f8af" />


**Question 3**
---
-- How many prescriptions were written in each frequency category (e.g., once daily, twice daily)?

-- select Frequency, count(PatientID) as TotalPrescriptions
FROM Prescriptions
group by Frequency;
```

**Output:**
<img width="786" height="530" alt="451344939-c0bff40e-f88d-42bc-a8d2-a0790c66f765" src="https://github.com/user-attachments/assets/68fc73f5-bc10-429a-bdd6-ccb2c94acf14" />



**Question 4**
---
-- Write a SQL query to find the average salary of all employees?

-- SELECT AVG(income) AS Average_Salary 
FROM employee;
```

**Output:**
<img width="500" height="311" alt="451345091-338edc65-45d5-4808-9499-9be884d9878a" src="https://github.com/user-attachments/assets/24ae4f84-b6d4-4138-8839-3c6af1a684bd" />



**Question 5**
---
-- Write a SQL query that counts the number of unique salespeople. Return number of salespeople.

-- SELECT count(distinct salesman_id) AS COUNT
FROM orders;
```

**Output:**
<img width="399" height="316" alt="451345354-faf627ff-1d61-437a-be90-6a2c300b885c" src="https://github.com/user-attachments/assets/911b8a37-b85d-47c8-bd79-dd5ed0cf0299" />



**Question 6**
---
-- Write a SQL query to return the total number of rows in the 'customer' table where the city is not Noida.

-- SELECT COUNT(id) AS COUNT FROM customer 
WHERE city != 'Noida';
```

**Output:**

<img width="394" height="311" alt="451345456-9cec0969-1b57-4d63-8520-ce9d54a168bc" src="https://github.com/user-attachments/assets/d654c8f7-a25d-4436-9cb9-f7d661d73a10" />


**Question 7**
---
-- Write a SQL query to find What is the age difference between the youngest and oldest employee in the company.

-- SELECT MAX(age) - MIN(age) AS age_difference 
FROM employee;
```

**Output:**

<img width="458" height="312" alt="451345619-2db69714-9ff2-467e-970f-c1113a4801dd" src="https://github.com/user-attachments/assets/c26ccedb-cac2-4be5-97b4-c8c63fdbe352" />


**Question 8**
---
--Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the minimum work hours for each date, and excludes dates where the minimum work hour is not less than 10.

-- SELECT jdate, MIN(workhour) 
FROM employee1 
GROUP BY jdate 
HAVING MIN(workhour) < 10;
```

**Output:**



**Question 9**
---
-- Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the total work hours for each date, and excludes dates where the total work hour sum is not greater than 40.

-- SELECT jdate, SUM(workhour)
FROM employee1 
GROUP BY jdate
HAVING SUM(workhour) >= 40;

```

**Output:**
<img width="636" height="373" alt="451345904-1c6e000f-0cb5-41f5-9358-3ca1f6c4d36a" src="https://github.com/user-attachments/assets/def2083f-c16b-441a-89e2-d93933e3ef55" />



**Question 10**
-- Write the SQL query that achieves the grouping of data by age, calculates the minimum income for each age group, and includes only those age groups where the minimum income is less than 400,000.

-- SELECT age, MIN(income) 
FROM employee 
GROUP BY age
HAVING MIN(income) < 400000;
```

**Output:**
<img width="565" height="333" alt="451346026-803d818b-9d1f-4472-93f6-4eaf2daa37fc" src="https://github.com/user-attachments/assets/51862211-889c-4e57-870f-530e2b05bebc" />




## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
