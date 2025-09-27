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
Write an SQL query to add a new column email of type TEXT to the Student_details table, and ensure that this column cannot contain NULL values and make default value as 'Invalid'

```sql
alter table student_details add column email TEXT not NULL default('Invalid');
```

**Output:**

<img width="1222" height="317" alt="image" src="https://github.com/user-attachments/assets/b717d516-d0a1-4eac-8d94-4d2acf4b4a0a" />



**Question 2**
---
Insert a product with ProductID 104, Name Tablet, and Category Electronics into the Products table, where Price and Stock should use default values.

```sql
insert into Products values('104',"Tablet","Electronics",'100','50');
```

**Output:**

<img width="1215" height="306" alt="image" src="https://github.com/user-attachments/assets/4a9d956c-d235-45e4-938e-082966d70a70" />

**Question 3**
---
Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should cascade updates and deletes.
item_desc and rate should not accept NULL.

```sql
create table item(
item_id TEXT primary key,
item_desc TEXT not null,
rate INTEGER not null,
icom_id TEXT(4),
foreign key(icom_id) references company(com_id) ON UPDATE CASCADE ON DELETE CASCADE
);
```

**Output:**

<img width="1222" height="413" alt="image" src="https://github.com/user-attachments/assets/c95812be-8b67-4458-b43b-4bf5c5673668" />


**Question 4**
---
Create a table named ProjectAssignments with the following constraints:
AssignmentID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
AssignmentDate as DATE should be NOT NULL.

```sql
create table ProjectAssignments(
AssignmentID INTEGER primary key,
EmployeeID INTEGER,
ProjectID INTEGER,
AssignmentDate DATE not NULL,
foreign key(EmployeeID) references Employees(EmployeeID),
foreign key(ProjectID) references Projects(ProjectID)
);
```

**Output:**
<img width="1246" height="352" alt="image" src="https://github.com/user-attachments/assets/4a835587-f8d9-40ae-96db-d6e9296108cc" />


**Question 5**
---
Write a SQL query to Add a new column named "discount" with the data type DECIMAL(5,2) to the "customer" table.

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
 

```sql
alter table customer add column discount DECIMAL(5,2);
```

**Output:**

<img width="1220" height="431" alt="image" src="https://github.com/user-attachments/assets/854d2708-3323-4e33-9dd1-c7a5ca7b5a5c" />


**Question 6**
---
Create a table named Invoices with the following constraints:

InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
DueDate as DATE should be greater than the InvoiceDate.
Amount as REAL should be greater than 0.
```sql
create table Invoices(
InvoiceID INTEGER primary key,
InvoiceDate DATE,
DueDate DATE check(DueDate>InvoiceDate),
Amount REAL check(Amount>0)
);
```

**Output:**

<img width="1221" height="370" alt="image" src="https://github.com/user-attachments/assets/86e868d2-8aee-4b33-ad49-041d80aa3bfc" />


**Question 7**
---
In the Books table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

ISBN             Title                      Author           Publisher   Year
---------------  -------------------------  ---------------  ----------  ----------
978-1234567890   Introduction to AI         John Doe
978-9876543210   Deep Learning              Jane Doe         TechPress   2022
978-1122334455   Cybersecurity Essentials   Alice Smith                  2021

```sql
insert into Books values('978-1234567890',"Introduction to AI ","John Doe",NUll,NULL);
insert into Books values('978-9876543210',"Deep Learning","Jane Doe","TechPress",'2022');
insert into Books values('978-1122334455',"Cybersecurity Essentials","Alice Smith",NULL,'2021');
```

**Output:**
<img width="1222" height="372" alt="image" src="https://github.com/user-attachments/assets/aa1a22ca-8ca4-4f23-98dd-e65f770df629" />


**Question 8**
---
Insert all products from Discontinued_products into Products.

Table attributes are ProductID, ProductName, Price, Stock



```sql
insert into products( ProductID, ProductName, Price, Stock)select ProductID,ProductName,Price,Stock from  Discontinued_products
```

**Output:**

<img width="1228" height="357" alt="image" src="https://github.com/user-attachments/assets/0a00b2f2-7ed2-4a3c-bb9b-4f6cf6e074a9" />


**Question 9**
---
Create a table named Departments with the following columns:

DepartmentID as INTEGER
DepartmentName as TEXT

```sql
create table Departments(
DepartmentID INTEGER,
DepartmentName TEXT
);
```

**Output:**
<img width="1243" height="451" alt="image" src="https://github.com/user-attachments/assets/1ff49fa5-1970-4a52-a224-37373101e06f" />



**Question 10**
---
Create a table named Attendance with the following constraints:
AttendanceID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
AttendanceDate as DATE.
Status as TEXT should be one of 'Present', 'Absent', 'Leave'.
```sql
create table Attendance(
AttendanceID INTEGER primary key,
EmployeeID INTEGER,
AttendanceDate DATE,
Status TEXT CHECK(Status IN ('Present','Absent','Leave')),
foreign key(EmployeeID) references Employees(EmployeeID) );
```

**Output:**

<img width="1246" height="363" alt="image" src="https://github.com/user-attachments/assets/ed8b0c81-98d2-4051-824f-d84f6ac248bc" />



## RESULT
<img width="673" height="183" alt="image" src="https://github.com/user-attachments/assets/0b5281a4-6541-47cc-83a0-1a192442ff78" />

Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
