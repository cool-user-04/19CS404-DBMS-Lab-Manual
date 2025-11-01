# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
<img width="1112" height="608" alt="440257960-6a7d531f-ab7a-4676-a915-51cf6a349ce5" src="https://github.com/user-attachments/assets/0f65140a-2a1e-4717-a5cb-e30d32d41b78" />
SELECT 
    customer.cust_name AS "Customer Name", 
    customer.city AS "city", 
    salesman.name AS "Salesman", 
    salesman.commission
FROM 
    customer
JOIN 
    salesman
ON 
    customer.salesman_id = salesman.salesman_id
WHERE 
    salesman.commission > 0.12;
```

**Output:**
<img width="885" height="467" alt="440258021-17930339-1ff8-4711-a2b1-f114420b8203" src="https://github.com/user-attachments/assets/0eb5558f-c7cb-474e-9d0a-6267d4865c86" />


**Question 2**
---
<img width="1333" height="448" alt="440258115-d3242b2e-3391-4cb3-a605-416836846233" src="https://github.com/user-attachments/assets/fbc1fe3a-d897-4f1f-8065-d694cf43d3b6" />

SELECT 
    patients.date_of_birth, 
    appointments.*
FROM 
    patients
JOIN 
    appointments
ON 
    patients.patient_id = appointments.patient_id
WHERE 
    patients.first_name = 'Alice';
```

**Output:**
<img width="1143" height="220" alt="440258250-f39c1ec5-21f6-490f-97fa-aa19952d99b8" src="https://github.com/user-attachments/assets/a10f10f4-1e8c-494f-89f2-b2caa184f46d" />


**Question 3**
---
<img width="890" height="655" alt="440258285-097557ad-6d0d-4e7c-b56e-8bff11cd916f" src="https://github.com/user-attachments/assets/da2a89c9-67ab-4932-a6ea-020565255c08" />

SELECT 
    orders.ord_no, 
    orders.ord_date, 
    orders.purch_amt, 
    customer.cust_name AS "Customer Name", 
    customer.grade, 
    salesman.name AS "Salesman", 
    salesman.commission
FROM 
    orders
JOIN 
    customer ON orders.customer_id = customer.customer_id
JOIN 
    salesman ON orders.salesman_id = salesman.salesman_id;
**Output:**
<img width="1318" height="761" alt="440258362-1bb423b5-b96f-453c-8285-9846debb43d7" src="https://github.com/user-attachments/assets/035b2c2a-046d-4c09-bafc-ce15319e2678" />



**Question 4**
---
<img width="1215" height="385" alt="440258377-cc381617-fa50-4692-96e2-8bffba32000c" src="https://github.com/user-attachments/assets/903e6268-a81c-4e7e-bfab-a84b5eee430b" />
SELECT 
    customer.cust_name, 
    customer.city, 
    customer.grade, 
    salesman.name AS "Salesman", 
    salesman.city AS "city"
FROM 
    customer
JOIN 
    salesman ON customer.salesman_id = salesman.salesman_id
WHERE 
    customer.grade < 300
ORDER BY 
    customer.customer_id ASC;
```

**Output:**
<img width="1026" height="462" alt="440258424-d0cfb6e4-ef2e-43e5-b0e9-5a2874ba62b7" src="https://github.com/user-attachments/assets/4034702c-430e-428b-be85-58425837b713" />



**Question 5**
---
<img width="1297" height="273" alt="440258468-64fc32f2-45b3-4f9d-9954-cb543e52f9a4" src="https://github.com/user-attachments/assets/de5ab55c-72e5-40ea-8ce4-c61667a47860" />
SELECT 
    s.name
FROM 
    salesman AS s
LEFT JOIN 
    customer AS c ON s.salesman_id = c.salesman_id
WHERE 
    c.city = 'London';
```

**Output:**
<img width="270" height="267" alt="440258507-6d8fbe7c-6d7e-4108-a9d9-4f40df26eadd" src="https://github.com/user-attachments/assets/3bcaebfa-d455-43db-be36-ddb389374f11" />



**Question 6**
---
<img width="971" height="259" alt="440258559-3676007b-6cbb-4aaa-be38-be3b7490a343" src="https://github.com/user-attachments/assets/abe10f33-2d16-4c1e-afa9-0cd875d68702" />
SELECT 
    c.cust_name
FROM 
    customer AS c
LEFT JOIN 
    orders AS o ON c.customer_id = o.customer_id;
```

**Output:**
<img width="274" height="759" alt="440258618-04dc1a46-1a8c-434a-ba1b-0a2ec097d8de" src="https://github.com/user-attachments/assets/2bdc1b75-f64f-4a56-a3ab-0c49ee59182d" />



**Question 7**
---
<img width="1560" height="360" alt="440258638-975eee13-6675-4d54-b674-ec9078a29105" src="https://github.com/user-attachments/assets/d64cb8cc-7e1e-4937-9a69-63ddd813fbdf" />
SELECT 
    p.first_name AS patient_name, 
    t.*
FROM 
    patients AS p
INNER JOIN 
    test_results AS t ON p.patient_id = t.patient_id;
```

**Output:**
<img width="1370" height="367" alt="440258907-67823836-4e83-4be1-a1ae-a33de5189991" src="https://github.com/user-attachments/assets/8818bb08-9b11-4ebc-8084-bb8322b4146c" />



**Question 8**
---

<img width="1154" height="459" alt="440259062-2cd468b9-1846-4cad-a2ae-49cfc5db6f79" src="https://github.com/user-attachments/assets/6f63683d-926b-493c-b56c-11acfc1408e7" />

SELECT 
    c.cust_name, 
    c.city AS city, 
    c.grade, 
    s.name AS Salesman, 
    s.city AS city
FROM 
    customer c
LEFT JOIN 
    salesman s 
ON 
    c.salesman_id = s.salesman_id
ORDER BY 
    c.customer_id ASC;
```

**Output:**
<img width="1202" height="657" alt="440259135-71369dc3-8140-495d-bfd5-3528da1c1715" src="https://github.com/user-attachments/assets/194df7e7-1819-4872-a431-5527ae64d074" />



**Question 9**
---

<img width="1300" height="435" alt="440259159-1c055a9f-cf86-4140-8ae1-0578c3d74740" src="https://github.com/user-attachments/assets/d252c14d-62ff-4740-a576-2f143c7f2bd0" />
SELECT 
    p.admission_date, 
    s.surgery_date
FROM 
    patients p
INNER JOIN 
    surgeries s 
ON 
    p.patient_id = s.patient_id;
```

**Output:**
<img width="555" height="368" alt="440259212-7a9059e3-1ca2-43bc-9473-ff3cd0245120" src="https://github.com/user-attachments/assets/94e5a6fc-ca16-45f3-8db4-40df7b9796ff" />


**Question 10**
---
SELECT 
    c.cust_name AS "Customer Name", 
    c.city, 
    s.name AS "Salesman", 
    s.commission
FROM 
    customer c
JOIN 
    salesman s 
ON 
    c.salesman_id = s.salesman_id;
<img width="1041" height="464" alt="440259238-6e570580-23be-4f6e-86db-1f7a43afc23c" src="https://github.com/user-attachments/assets/4f4694d7-336a-412e-8e0c-2f90d5bf7d43" />

```

**Output:**

<img width="1037" height="660" alt="440259292-f2ed3a8d-50ee-4576-b936-9dfde3589de2" src="https://github.com/user-attachments/assets/33c0f863-6bc1-4570-a560-3d9786f6da02" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
