# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
--
Write a SQL statement to Update the address to '58 Lakeview, Magnolia' where supplier ID is 5 in the suppliers table.

Suppliers Table

name type
supplier_id INT supplier_name VARCHAR(100) contact_person VARCHAR(100) phone_number VARCHAR(20) email VARCHAR(100) address VARCHAR(250)

update Suppliers
set address='58 Lakeview, Magnolia'
where supplier_id=5;
```

**Output:**
<img width="1307" height="260" alt="501280195-29c8b7e2-f7dd-47a0-a8d3-15163c0d6dab" src="https://github.com/user-attachments/assets/f45a2470-0c20-4740-8537-787238406bf7" />



**Question 2**
---
Write a SQL statement to Increase the salary by 500 and email as 'updated' for employees with job ID 'SA_REP' and commission percentage greater than 0.15

Employees table

employee_id first_name last_name email phone_number hire_date job_id salary commission_pct manager_id department_id

update Employees
SET SALARY=SALARY+500,
EMAIL='updated'
WHERE JOB_ID='SA_REP' AND
COMMISSION_PCT>0.15;
```

**Output:**
<img width="1222" height="317" alt="501280386-0fe2c9a7-1901-4eb5-9f34-c21317a89484" src="https://github.com/user-attachments/assets/e9b1c6a4-9aa3-46e1-92af-c515b1869a6d" />


**Question 3**
---
For Increase the selling price per unit by 3 for all products supplied by supplier ID 4 in the sales table.

PRODUCTS TABLE

name type
product_id INT product_name VARCHAR(100) category VARCHAR(50) cost_price DECIMAL(10,2) sell_price DECIMAL(10,2) reorder_lvl INT quantity INT supplier_id INT

SALES TABLE name type

sale_id INT sale_date DATE product_id INT quantity INT sell_price DECIMAL(10,2) total_sell_price DECIMAL(10,2)

update SALES
set sell_price=sell_price+3
where product_id IN(
    select product_id
    from PRODUCTS
    WHERE supplier_id=4
);
```

**Output:**
<img width="1295" height="242" alt="501280590-9ee41a54-542a-415d-948b-c8009ff687e2" src="https://github.com/user-attachments/assets/2743c1bd-36a2-4469-b5e5-1ec6c147be1e" />


**Question 4**
---
Change the supplier name to upper case where contact person contains ' Singh' in suppliers table.

name type

supplier_id INT supplier_name VARCHAR(100) contact_person VARCHAR(100) phone_number VARCHAR(20) email VARCHAR(100) address VARCHAR(250)

update suppliers
set supplier_name=UPPER(supplier_name)
where contact_person LIKE '%Singh%'
```

**Output:**
<img width="1296" height="230" alt="501280855-e2f6a0fe-9899-493f-8a9c-213b02e90730" src="https://github.com/user-attachments/assets/7e63a7b1-5e0d-4313-9506-f2fe72233b05" />



**Question 5**
---
Write a SQL statement to change salary of employee to 8000 whose Employee ID is 105, if the existing salary is less than 5000.

Employees table

employee_id first_name last_name email phone_number hire_date job_id salary commission_pct manager_id department_id

update Employees
set salary=8000
where employee_id=105 and salary<5000;
```

**Output:**
<img width="1257" height="130" alt="501281016-65686a04-fa60-430a-83fa-0d62fe7a80f7" src="https://github.com/user-attachments/assets/2ce4a234-16c7-41e1-a0a8-d1315935102e" />



**Question 6**
---
Write a SQL query to Delete customers with 'GRADE' 3 or 'AGENT_CODE' 'A008' whose 'OUTSTANDING_AMT' is less than 5000

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+---------- |CUST_CODE | CUST_NAME | CUST_CITY | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO | AGENT_CODE | +-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+----------- | C00013 | Holmes | London | London | UK | 2 | 6000.00 | 5000.00 | 7000.00 | 4000.00 | BBBBBBB | A003 | | C00001 | Micheal | New York | New York | USA | 2 | 3000.00 | 5000.00 | 2000.00 | 6000.00 | CCCCCCC | A008 | | C00020 | Albert | New York | New York | USA | 3 | 5000.00 | 7000.00 | 6000.00 | 6000.00 | BBBBSBB | A008 |
```
delete from customer
where(GRADE=3 OR AGENT_CODE = 'A008')
AND OUTSTANDING_AMT<5000;
**Output:**
<img width="1325" height="282" alt="501281214-cef309a1-781a-48ce-8763-9400c1446132" src="https://github.com/user-attachments/assets/60bc9e90-9986-4a49-83e0-53d229e96892" />



**Question 7**
---
Write a SQL query to delete a doctor from Doctors table whose Specialization is 'Pediatrics' and First name is 'Michael'.

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization
delete from Doctors where Specialization='Pediatrics' and first_name like "%Michael";
```

**Output:**
<img width="840" height="227" alt="501281339-0d4dc596-57e3-4736-8897-736ae14f6803" src="https://github.com/user-attachments/assets/60c4ed00-4257-4d75-a82a-998926818d43" />



**Question 8**
---
Write a SQL query to Delete customers with following conditions

'CUST_COUNTRY' is not in a list of specified countries ('UK', 'USA', 'Canada') 'GRADE' is greater than or equal to 3 Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
|CUST_CODE | CUST_NAME | CUST_CITY | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO | AGENT_CODE | +-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+ | C00013 | Holmes | London | London | UK | 2 | 6000.00 | 5000.00 | 7000.00 | 4000.00 | BBBBBBB | A003 | | C00001 | Micheal | New York | New York | USA | 2 | 3000.00 | 5000.00 | 2000.00 | 6000.00 | CCCCCCC | A008 | | C00020 | Albert | New York | New York | USA | 3 | 5000.00 | 7000.00 | 6000.00 | 6000.00 | BBBBSBB | A008 |
delete from Customer
where CUST_COUNTRY NOT IN('UK','USA','Canada')
    AND GRADE>=3;
```

**Output:**
<img width="1316" height="277" alt="501281553-2c42e38e-b51a-40fc-a552-0493a2ac7734" src="https://github.com/user-attachments/assets/be469764-cf03-494d-81e7-d683b0e62d80" />



**Question 9**
---
Write a SQL query to Delete a Specific Surgery whose ID is 3

Sample table: Surgeries

attributes: surgery_id, patient_id, surgeon_id, surgery_date

delete from surgeries
where surgery_id=3;
```

**Output:**
<img width="852" height="229" alt="501281690-58de98a5-73f4-41f3-bc79-4d1e2b20f96e" src="https://github.com/user-attachments/assets/cebf6f7e-e28f-481c-87d2-6478f129e470" />



**Question 10**
---
Write a SQL query to Delete customers with 'CUST_COUNTRY' 'UK' and 'WORKING_AREA' 'London' whose 'GRADE' is less than 3

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
|CUST_CODE | CUST_NAME | CUST_CITY | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO | AGENT_CODE | +-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+ | C00013 | Holmes | London | London | UK | 2 | 6000.00 | 5000.00 | 7000.00 | 4000.00 | BBBBBBB | A003 | | C00001 | Micheal | New York | New York | USA | 2 | 3000.00 | 5000.00 | 2000.00 | 6000.00 | CCCCCCC | A008 | | C00020 | Albert | New York | New York | USA | 3 | 5000.00 | 7000.00 | 6000.00 | 6000.00 | BBBBSBB | A008 |

delete from Customer
where CUST_COUNTRY='UK'
AND WORKING_AREA='London'
AND GRADE<3;
```

**Output:**

<img width="1311" height="311" alt="501281877-d05f46ad-a16e-423b-855f-09fbd2859dc9" src="https://github.com/user-attachments/assets/c3223c86-a8ea-4929-b307-4592fdeab72a" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
