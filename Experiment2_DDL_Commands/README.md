# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--
<img width="1187" height="307" alt="438551416-1ff73ec5-f6a1-4e70-9010-161c6f3772f6" src="https://github.com/user-attachments/assets/0db465f4-a7dc-4d1b-a906-46a3701612fd" />


```sql
--
INSERT INTO Employee(EmployeeID,Name,Position)
values(5,           'George Clark',  'Consultant');

INSERT INTO Employee(EmployeeID,Name,Position,Department,Salary)
values(7,           'Noah Davis',    'Manager',     'HR',          60000);

INSERT INTO Employee(EmployeeID,Name,Position,Department)
values(8,           'Ava Miller',    'Consultant',  'IT');
```

**Output:**
<img width="1253" height="175" alt="438616641-89435e54-9c59-4711-bc20-d0f6f9f6e311" src="https://github.com/user-attachments/assets/7de1ae06-13ce-4ff2-aceb-0e3178328427" />



**Question 2**
---
<img width="1221" height="406" alt="438543003-ca0a9da9-7501-4266-ba08-645feed50fd9" src="https://github.com/user-attachments/assets/7e18913f-912b-4659-bc65-da0e9fbad89d" />
-- 
CREATE TABLE Attendance (  
    AttendanceID INTEGER PRIMARY KEY,  
    EmployeeID INTEGER,  
    AttendanceDate DATE,  
    Status TEXT CHECK (Status IN ('Present', 'Absent', 'Leave')),  
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID)  
);
```

**Output:**
<img width="1247" height="382" alt="438539788-c39daf8f-3430-4210-a8ff-d01b24a63277" src="https://github.com/user-attachments/assets/10d0801e-ca4c-4310-be0f-b6d62c4a1b41" />



**Question 3**
---
<img width="1140" height="358" alt="438542915-dae1d226-9026-4d29-9254-7de0910c737f" src="https://github.com/user-attachments/assets/bff3b51a-5c99-453d-b3fc-a0c3224f7af2" />
--
ALTER TABLE Employees
ADD COLUMN Date_of_joining Date;

ALTER TABLE Employees
RENAME COLUMN job_title To Designation;

```

**Output:**
<img width="1220" height="415" alt="438540080-34ffec3a-d6f4-4db9-a215-4b0e07cf2498" src="https://github.com/user-attachments/assets/e243ed50-99df-4677-b032-567b6502bee1" />



**Question 4**
---
<img width="1394" height="349" alt="438542847-5269cf0c-35ef-423a-8f4d-e23d598326c0" src="https://github.com/user-attachments/assets/b204120e-4a22-4f9e-a298-b547c533d3f8" />
--
 CREATE TABLE jobs (  
    job_id INTEGER PRIMARY KEY,  
    job_title TEXT NOT NULL DEFAULT '',  
    min_salary INTEGER NOT NULL DEFAULT 8000,  
    max_salary INTEGER DEFAULT NULL  
);
```

**Output:**

<img width="1252" height="434" alt="438540313-6ac5521f-2c29-4742-8243-8b4e41797c86" src="https://github.com/user-attachments/assets/52a5e7df-0af0-41f6-a607-2c34416a15f1" />


**Question 5**
---
<img width="1485" height="381" alt="438542784-df2640c1-2236-4197-a730-8d3801cdb17b" src="https://github.com/user-attachments/assets/cccb120a-0def-4eff-a36e-45bf770e3391" />
--
CREATE TABLE Departments(
DepartmentID INTEGER,
DepartmentName TEXT
);
```

**Output:**
<img width="1236" height="442" alt="438540767-455829b4-4134-45de-b480-5692c256072d" src="https://github.com/user-attachments/assets/12fd8e98-1c91-42f6-bd64-02c3494c93f7" />



**Question 6**
---
<img width="1063" height="350" alt="438542740-9e2758a1-6ee5-4c45-8061-abac41022770" src="https://github.com/user-attachments/assets/85d96103-649b-4fc5-a1a9-49c2c5ad6423" />
-
select *from Out_of_print_books
union all
select *from Books
```

**Output:**

<img width="1229" height="380" alt="438541479-151cdda8-17c8-4153-9df3-34567f3eaa0f" src="https://github.com/user-attachments/assets/ef82330f-de17-4ab9-ad99-11e3469e65a1" />


**Question 7**
---
<img width="1075" height="454" alt="438542685-c8c69844-81cf-4cf9-8eba-a0b0d0bb6701" src="https://github.com/user-attachments/assets/e7e64f14-3860-476f-ba09-0af3702ab8d4" />
--
CREATE TABLE item (  
    item_id TEXT PRIMARY KEY,  
    item_desc TEXT NOT NULL,  
    rate INTEGER NOT NULL,  
    icom_id TEXT CHECK(4),  
    FOREIGN KEY (icom_id) REFERENCES company(com_id)  
    ON UPDATE CASCADE  
    ON DELETE CASCADE  
);
```

**Output:**
<img width="1236" height="438" alt="438541764-4880a2ef-a33b-4cc3-b31c-216f255b2b67" src="https://github.com/user-attachments/assets/c2138ca5-d163-4de6-9b60-f97540d1de38" />



**Question 8**
---
<img width="1099" height="297" alt="438542632-7096c7b2-8067-45fb-95ce-c61bec119446" src="https://github.com/user-attachments/assets/6795dda4-581d-493a-beb8-b78185140562" />
--
ALTER TABLE employee
ADD COLUMN designation varchar(50);
```

**Output:**
<img width="1242" height="375" alt="438542140-0f2267dc-bc94-49e4-84e3-2a143335f3cf" src="https://github.com/user-attachments/assets/2ace17cc-00d6-42b3-9ec9-26e6184485ac" />



**Question 9**
---
<img width="1243" height="289" alt="438542206-06d2e58d-4853-4ba5-9d54-f03e0c410af6" src="https://github.com/user-attachments/assets/7c3d4a6a-5e16-4ddc-995b-ad084d4c67d1" />
--
INSERT INTO Products (ProductID, Name, Category)  
VALUES (104, 'Tablet', 'Electronics');
```

**Output:**

<img width="1270" height="326" alt="438542302-439c6599-0b13-49c7-95a4-3d53ecfde7bc" src="https://github.com/user-attachments/assets/b34a41f2-5433-4105-b261-5afbab61e21d" />


**Question 10**
---
<img width="1232" height="396" alt="438542367-9424a09d-c763-4283-85b1-287761ae025d" src="https://github.com/user-attachments/assets/7ef51e0e-08be-458b-b039-4133b0138282" />

--
CREATE TABLE Employees(
EmployeeID INTEGER primary key,
FirstName INTEGER NOT NULL,
LastName INTEGER NOT NULL,
Email VARCHAR(50) unique,
Salary CHECK (Salary>0),
DepartmentID INTEGER,
foreign key(DepartmentID) references Departments(DepartmentID)
);
```

**Output:**

<img width="1234" height="488" alt="438543486-8631abbc-db12-4fe7-bbf9-06bffaa06c5a" src="https://github.com/user-attachments/assets/2cf0034c-dea4-42ef-a620-acade2d7ec55" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
