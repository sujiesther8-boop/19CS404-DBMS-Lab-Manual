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
--Decrease the reorder level by 30 percent where the product name contains 'cream' and quantity in stock is higher than reorder level in the products table.

PRODUCTS TABLE

name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT
-- 

```sql
-- UPDATE products
SET reorder_lvl = reorder_lvl * 0.70
WHERE product_name LIKE '%cream%'
  AND quantity > reorder_lvl;
```

**Output:**
<img width="992" height="462" alt="image" src="https://github.com/user-attachments/assets/5e4771e9-7bbb-4157-b313-68336dc3b6ec" />


**Question 2**
---Write a SQL statement to Update the hire_date of employees in department 50 to 2024-01-24.


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
--

```sql
-- UPDATE Employees
SET hire_date = '2024-01-24'
WHERE department_id = 50;
```

**Output:**
<img width="751" height="285" alt="image" src="https://github.com/user-attachments/assets/11453590-7f10-447e-a1b5-ee3c0d46ff5e" />



**Question 3**
---
--Write a SQL query to calculate the final price after applying both the discount and the tax. Return product_id, original_price, discount_percentage, tax_rate, and final_price.

Sample table: Products

product_id | original_price | discount_percentage | tax_rate

 ------------+----------------+---------------------+--------- 

101 | 50.00 | 0.10 | 0.08 

102 | 75.00 | 0.15 | 0.05 

103 | 100.00 | 0.20 | 0.10

```sql
--SELECT
    product_id,
    original_price,
    discount_percentage,
    tax_rate,
    original_price * (1 - discount_percentage) * (1 + tax_rate) AS final_price
FROM Products;
```

**Output:**
<img width="1161" height="262" alt="image" src="https://github.com/user-attachments/assets/b07b115f-ae02-4913-a947-466f97f282ed" />


**Question 4**
---
-- write a SQL query to find details of all orders with a purchase amount less than 200 or exclude orders with an order date greater than or equal to '2012-02-10' and a customer ID less than 3009. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id
----------  ----------  ----------  -----------  -----------
70001       150.5       2012-10-05  3005         5002
70009       270.65      2012-09-10  3001         5005
70002       65.26       2012-10-05  3002         5001

```sql
-- SELECT ord_no, purch_amt, ord_date, customer_id, salesman_id
FROM orders
WHERE purch_amt < 200
   OR NOT (ord_date >= '2012-02-10' AND customer_id < 3009);
```

**Output:**
<img width="1167" height="442" alt="image" src="https://github.com/user-attachments/assets/b097dba8-5aeb-46c3-9ed1-976401188aa3" />


**Question 5**
---
--Write a SQL query to select patient's names along with their age groups (e.g., 'Under 20', '20-30', '31-40', '41-50', 'Above 50') based on their date of birth. 

Note: Consider current date as '2023-12-30' while calculating age.

Table: Patients

name                  type
--------------------  ----------
patient_id            INT
first_name            VARCHAR(50
last_name             VARCHAR(50
date_of_birth         DATE
admission_date        DATE
discharge_date        DATE
doctor_id             INT

```sql
-- SELECT
    first_name,
    last_name,
    CASE
        WHEN (julianday('2023-12-30') - julianday(date_of_birth)) / 365.25 < 20
            THEN 'Under 20'
        WHEN (julianday('2023-12-30') - julianday(date_of_birth)) / 365.25 <= 30
            THEN '20-30'
        WHEN (julianday('2023-12-30') - julianday(date_of_birth)) / 365.25 <= 40
            THEN '31-40'
        WHEN (julianday('2023-12-30') - julianday(date_of_birth)) / 365.25 <= 50
            THEN '41-50'
        ELSE 'Above 50'
    END AS AgeGroup
FROM Patients;
```

**Output:**
<img width="773" height="385" alt="image" src="https://github.com/user-attachments/assets/62222bef-1996-489c-925b-b1da706bd7bf" />


**Question 6**
---
--Write a SQL query to delete a specific doctor from Doctors table whose ID is 1.

Sample table: Doctors

attributes: doctor_id, first_name, last_name, specialization


```sql
DELETE FROM Doctors
WHERE doctor_id = 1;
```

**Output:**
<img width="1178" height="232" alt="image" src="https://github.com/user-attachments/assets/aaa954c6-66f1-4594-b83d-7ac8f3a38cb9" />

**Question 7**
---
--Write a SQL query to Get the first three characters of each unique job title:

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
--SELECT DISTINCT
    job,
    SUBSTR(job, 1, 3) AS job_abbr
FROM emp;
```

**Output:**
<img width="560" height="502" alt="image" src="https://github.com/user-attachments/assets/9550d111-7241-4f24-8716-8a134c75d3ce" />


**Question 8**
---
--Write a SQL query to delete a doctor from Doctors table whose Specialization is 'Pediatrics' and First name is 'Michael'.

Sample table: Doctors

attributes: doctor_id, first_name, last_name, specialization

```sql
--DELETE FROM Doctors
WHERE specialization = 'Pediatrics'
  AND first_name = 'Michael';
```

**Output:**
 <img width="1173" height="363" alt="image" src="https://github.com/user-attachments/assets/b7d65009-c3ca-474d-a316-56013f3391c8" />


**Question 9**
---
-- Write a SQL statement to change salary of employee to 8000 whose Employee ID is 105, if the existing salary is less than 5000.


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
--UPDATE Employees
SET salary = 8000
WHERE employee_id = 105
  AND salary < 5000;
```

**Output:**
<img width="1013" height="201" alt="image" src="https://github.com/user-attachments/assets/6bd2c2c4-b219-45d6-a594-e1ba6f6e950a" />

**Question 10**
---
--Write a SQL statement to display name and commission of first 5 salesmen.

table info

salesman(name,commission) 

```sql
--SELECT name, commission
FROM salesman
LIMIT 5;
```

**Output:**
<img width="585" height="397" alt="image" src="https://github.com/user-attachments/assets/92911063-0f4e-4b12-b77e-0fa8b5330a33" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
