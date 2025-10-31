# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
--
Write a SQL query to Retrieve the medications with dosages equal to the highest dosage

Table Name: Medications (attributes: medication_id, medication_name, dosage)



```sql
select medication_id, medication_name, dosage from Medications where dosage =(select max(dosage) from Medications);
```

**Output:**

<img width="851" height="312" alt="image" src="https://github.com/user-attachments/assets/fd18eb53-5249-429c-bbc7-8c096eb0fa87" />


**Question 2**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is EQUAL TO $1500.

```sql
select * from customers where salary='1500';
```

**Output:**


<img width="1202" height="326" alt="image" src="https://github.com/user-attachments/assets/c30c3ae2-8c29-47ea-b4f2-aa153de0f73e" />


**Question 3**
---
From the following tables write a SQL query to find the order values greater than the average order value of 10th October 2012. Return ord_no, purch_amt, ord_date, customer_id, salesman_id.

Note: date should be yyyy-mm-dd format

```sql
select ord_no, purch_amt, ord_date, customer_id, salesman_id from orders where purch_amt>(select avg(purch_amt) from orders where ord_date='2012-10-10');
```

**Output:**

<img width="1228" height="440" alt="image" src="https://github.com/user-attachments/assets/81d36b5e-21b1-444b-982c-4d6d164f967c" />



**Question 4**
---
Write a SQL query to Identify customers whose city is different from the city of the customer with the highest ID

SAMPLE TABLE: customer

name             type
---------------  ---------------
id               INTEGER
name             TEXT
city             TEXT
email            TEXT
phone            INTEGER

```sql
select * from customer where city <>(select city from customer where id=(select max(id) from customer));
```

**Output:**

<img width="1238" height="477" alt="image" src="https://github.com/user-attachments/assets/3057822d-0e78-4084-8259-85991cd27e05" />


**Question 5**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is LESS than $2500.

```sql
select * from customers where salary<2500;
```

**Output:**
<img width="1233" height="441" alt="image" src="https://github.com/user-attachments/assets/626e9c4f-0313-4c30-b0aa-82bf1166fdda" />

**Question 6**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose Address as Delhi

```sql
select * from customers where address='Delhi';
```

**Output:**
<img width="1267" height="343" alt="image" src="https://github.com/user-attachments/assets/41c3da37-7cca-4a2d-a27c-29887c78ffe6" />



**Question 7**
---
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is greater than $4500.


```sql
select * from customers where salary>4500;
```

**Output:**

<img width="1257" height="431" alt="image" src="https://github.com/user-attachments/assets/c86c1192-2bc1-4649-b5af-2d916e80aa92" />


**Question 8**
---
Write a SQL query to Find employees who have an age less than the average age of employees with incomes over 1 million

```sql
select * from employee where age<(select avg(age) from employee where income>'1000000');
```

**Output:**
<img width="1235" height="412" alt="image" src="https://github.com/user-attachments/assets/117acb38-4757-4cdb-b2c2-b6f938bda86e" />


**Question 9**
---
Write a SQL query to Find employees who have an age less than the average age of employees with incomes over 2.5 Lakhs

```sql
select * from employee where age<(select avg(age) from employee where income>250000);
```

**Output:**
<img width="1230" height="492" alt="image" src="https://github.com/user-attachments/assets/95c00860-f03e-4034-b838-fb4f7a9edf91" />


**Question 10**
---
Write a query to display all the customers whose ID is the difference between the salesperson ID of Mc Lyon and 2001.
```sql
SELECT *
FROM customer
WHERE customer_id = (
    SELECT salesman_id - 2001
    FROM salesman
    WHERE name = 'Mc Lyon'
);
```

**Output:**

<img width="1236" height="318" alt="image" src="https://github.com/user-attachments/assets/a53642ba-de3d-4e7d-bc77-33a9ad057259" />



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
