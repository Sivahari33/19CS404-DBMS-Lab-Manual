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
Write a SQL statement to update the product_name as 'Grapefruit' whose product_id is 4 in the products table.

products table

---------------
product_id
product_name
category_id
availability

```sql
update products set product_name='Grapefruit' where product_id='4';
```

**Output:**

<img width="1221" height="242" alt="image" src="https://github.com/user-attachments/assets/2a9e18b9-d8c2-4aa7-a33d-3b2842415e05" />


**Question 2**
---
Write a SQL statement to Change the supplier name to 'A1 Suppliers' where the supplier ID is 8 in the suppliers table.

Table info

suppliers(supplier_id,supplier_name,contact_person,phone_number,email,address)

```sql
update suppliers set supplier_name='A1 Suppliers' where supplier_id='8';
```

**Output:**
<img width="1188" height="395" alt="image" src="https://github.com/user-attachments/assets/6a94282e-bd0c-4e13-85c2-ee13cc864c8c" />


**Question 3**
Write a SQL statement to Increase the selling price by 15% in the products table where quantity in stock is less than 50 and supplier ID is 10.

Products Table 

name          type       
----------    ---------- 
product_id     INT PRIMARY KEY        
product_name   VARCHAR(10) 
category       VARCHAR(50) 
cost_price     DECIMAL(10) 
sell_price     DECIMAL(10) 
reorder_lv     INT        
quantity       INT        
supplier_id    INT       

```sql
UPDATE Products
SET sell_price = sell_price * 1.15
WHERE quantity < 50
  AND supplier_id = 10;
```

**Output:**
<img width="1172" height="486" alt="image" src="https://github.com/user-attachments/assets/6fcac10f-cafd-4155-8def-28696eea0a6f" />

**Question 4**
---
Write a SQL statement to change the EMAIL and COMMISSION_PCT column of the following EMPLOYEES table with 'not available' and 0.55 for those employees whose DEPARTMENT_ID is 110.

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id

```sql
update Employees set email='not available',commission_pct='0.55' where department_id='110';
```

**Output:**
<img width="1200" height="393" alt="image" src="https://github.com/user-attachments/assets/2bd5480a-7f6a-4e0e-9318-e1df66e7c155" />


**Question 5**
---
Write a SQL query to delete a specific doctor from Doctors table whose ID is 1.

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization

```sql
delete from Doctors where doctor_id='1';
```

**Output:**

<img width="1207" height="258" alt="image" src="https://github.com/user-attachments/assets/10636777-ff46-4fec-a38f-b01ec1845100" />


**Question 6**
---
Write a SQL query to calculate the original price using the discount percentage and the given discounted price. Return product_id, discounted_price, discount_percentage, and original_price.

Sample table: Products

product_id | discounted_price | discount_percentage

 ------------+------------------+---------------------

 101 | 45.00 | 0.10 

102 | 63.75 | 0.15 

103 | 80.00 | 0.20

```sql
SELECT 
    product_id,
    discounted_price,
    discount_percentage,
    discounted_price / (1 - discount_percentage) AS original_price
FROM Products;
```

**Output:**

<img width="1212" height="283" alt="image" src="https://github.com/user-attachments/assets/62018b56-79f1-4f5e-8b4c-fef522132a9a" />


**Question 7**
---
Write a SQL query to calculate the discount amount for each product. Return product_id, original_price, discount_percentage, and discount_amount.

Sample table: Products

product_id | original_price | discount_percentage
------------+----------------+---------------------
101 | 50.00 | 0.10
102 | 75.00 | 0.15
103 | 100.00 | 0.20

```sql
SELECT 
    product_id,
    original_price,
    discount_percentage,
    original_price * discount_percentage AS discount_amount
FROM Products;
```

**Output:**

<img width="1187" height="267" alt="image" src="https://github.com/user-attachments/assets/3c3f0166-42ab-4fde-9027-637148b2791d" />


**Question 8**
---
Write a SQL query to find employees who were hired after January 1, 2020.

emp table

cid         name        type        
----------  ----------  ---------- 
0           empno       INT         
1           ename       VARCHAR(100)
2           job         VARCHAR(50)
3           mgr         INT        
4           hiredate    DATE        
5           sal         DECIMAL(10,2)  
6           comm        DECIMAL(10,2)  
7           deptno      INT      

```sql
SELECT *
FROM emp
WHERE hiredate > '2020-01-01';
```

**Output:**
<img width="1222" height="365" alt="image" src="https://github.com/user-attachments/assets/afee23c6-3e9a-4788-a43f-fd1657e144d1" />


**Question 9**
---
Write a SQL query to calculate the number of days between the hiredate and a specified date ('2024-12-31') for each employee using the JULIANDAY function from the emp table.

emp table

cid         name        type        
----------  ----------  ---------- 
0           empno       INT         
1           ename       VARCHAR(100)
2           job         VARCHAR(50)
3           mgr         INT        
4           hiredate    DATE        
5           sal         DECIMAL(10,2)  
6           comm        DECIMAL(10,2)  
7           deptno      INT         

```sql
SELECT 
    
    ename,
    hiredate,
    JULIANDAY('2024-12-31') - JULIANDAY(hiredate) AS days_worked
FROM emp;
```

**Output:**
<img width="763" height="187" alt="image" src="https://github.com/user-attachments/assets/156eb7b5-a390-4a0b-b359-8e67fa54b6e6" />


**Question 10**
---
Write a SQL query to Get the employee names where the first letter of each word is the same.

 
Table name: emp

name        type
----------  ----------
empno       INT
ename       VARCHAR(100)
job         VARCHAR(50)
mgr         INT
hiredate    DATE
sal         DECIMAL(10,2)
comm        DECIMAL(10,2)
deptno      INT

```sql
SELECT ename
FROM emp
WHERE 
    LOWER(SUBSTR(ename, 1, 1)) = LOWER(SUBSTR(SUBSTR(ename, INSTR(ename, ' ') + 1), 1, 1));
```

**Output:**
<img width="416" height="336" alt="image" src="https://github.com/user-attachments/assets/440fcf54-53b5-4c6d-a3d9-2b055a9341db" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
