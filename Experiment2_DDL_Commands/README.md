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
Create a table named Tasks with the following columns:

TaskID as INTEGER
TaskName as TEXT
DueDate as DATE

```sql
CREATE TABLE tasks(
TaskID INTEGER,
TaskName TEXT,
DueDate DATE
)
```

**Output:**
<img width="1182" height="362" alt="image" src="https://github.com/user-attachments/assets/a3738574-86da-4a1a-ad73-6ca18bed2b0e" />


**Question 2**
---
Write a SQL Query to add an attribute designation in the employee table with the data type VARCHAR(50).

```sql
-ALTER TABLE employee
ADD designation varchar(50)

```

**Output:**
<img width="1186" height="278" alt="image" src="https://github.com/user-attachments/assets/28d16e6a-b475-42ae-b7a2-b0683e51b771" />


**Question 3**
---
--Create a table named Reviews with the following columns:

ReviewID as INTEGER
ProductID as INTEGER
Rating as REAL
ReviewText as TEXT

```sql
-- CREATE TABLE Reviews(
ReviewID INTEGER,
ProductID INTEGER,
Rating REAL,
ReviewText TEXT
)
```

**Output:**
<img width="1163" height="373" alt="image" src="https://github.com/user-attachments/assets/d7a9203b-5c9a-4d33-b680-d0dd3628c9e6" />


**Question 4**
---

Insert all customers from Old_customers into Customers

Table attributes are CustomerID, Name, Address, Email
```
INSERT INTO Customers(CustomerID, Name, Address, Email)
SELECT CustomerID, Name, Address, Email
FROM Old_customers;
```
**Output:**

![image](https://github.com/user-attachments/assets/5ad04860-aab6-4066-9138-47629ff8a49f)

**Question 5**
---
--Write an SQL query to add two new columns, department_id and manager_id, to the table employee with datatype of INTEGER. The manager_id column should have a default value of NULL.

```sql
-- ALTER TABLE employee ADD COLUMN department_id INTEGER;
ALTER TABLE employee ADD COLUMN manager_id INTEGER DEFAULT NULL;
```

**Output:**
![image](https://github.com/user-attachments/assets/aa64eeea-195a-4162-91ea-0dd7a32aa315)

**Question 6**
---

 ---Write a SQL query to Add a new column named "discount" with the data type DECIMAL(5,2) to the "customer" table.

Sample table: customer

customer_id | cust_name | city | grade | salesman_id -------------+----------------+------------+-------+------------- 3002 | Nick Rimando | New York | 100 | 5001 3007 | Brad Davis | New York | 200 | 5001 3005 | Graham Zusi | California | 200 | 5002
```
ALTER TABLE customer  ADD COLUMN discount DECIMAL(5,2);
```

**Output:**

![image](https://github.com/user-attachments/assets/fc9f743c-666b-401b-84c5-983bd21a4926)

**Question 7**
---
--Insert a book with ISBN 978-1234567890, Title Data Science Essentials, Author Jane Doe, Publisher TechBooks, and Year 2024 into the Books table.

```sql
INSERT INTO Books(ISBN,Title,Author,Publisher,Year)
VALUES ( '978-1234567890','Data Science Essentials','Jane Doe','TechBooks',2024)

**Output:**
<img width="1180" height="222" alt="image" src="https://github.com/user-attachments/assets/4e696c7b-0059-4b33-b1bf-7ba8fb7251f3" />


**Question 8**
---
--Create a new table named products with the following specifications:
product_id as INTEGER and primary key.
product_name as TEXT and not NULL.
list_price as DECIMAL (10, 2) and not NULL.
discount as DECIMAL (10, 2) with a default value of 0 and not NULL.
A CHECK constraint at the table level to ensure:
list_price is greater than or equal to discount
discount is greater than or equal to 0
list_price is greater than or equal to 0

```sql
--CREATE TABLE products(
product_id INTEGER PRIMARY KEY,
product_name TEXT NOT NULL,
list_price DECIMAL (10,2) NOT NULL,
discount DECIMAL (10,2) NOT NULL DEFAULT 0,
CHECK(
 list_price>=discount
 AND discount>=0
 AND list_price>=0
)
);
```

**Output:**
<img width="942" height="257" alt="image" src="https://github.com/user-attachments/assets/314dc181-b170-401c-9d1e-24a0b6dde0a2" />


**Question 9**
---
--Insert the below data into the Student_details table, allowing the Subject and MARKS columns to take their default values.

RollNo      Name          Gender      
----------  ------------  ----------  
204         Samuel Black  M          

Note: The Subject and MARKS columns will use their default values.

```sql
--INSERT INTO Student_details(RollNo,Name,Gender)
VALUES(204,'Samuel Black','M')
```

**Output:**
<img width="1185" height="288" alt="image" src="https://github.com/user-attachments/assets/89617ed0-74d4-4724-931c-dd4fce9d6569" />


**Question 10**
---
--Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should cascade updates and deletes.
item_desc and rate should not accept NULL.

```sql
--CREATE TABLE item (
item_id TEXT PRIMARY KEY,
item_desc TEXT NOT NULL,
rate INTEGER NOT NULL,
icom_id TEXT(4),
FOREIGN KEY(icom_id)
       REFERENCES company(com_id)
       ON UPDATE CASCADE
       ON DELETE CASCADE

);
```

**Output:**
<img width="1181" height="347" alt="image" src="https://github.com/user-attachments/assets/c7dd13ea-fe13-4a97-a7ed-68e2d7503efe" />

## GRADES
<img width="1897" height="525" alt="image" src="https://github.com/user-attachments/assets/214f0ee7-b8cf-4117-805a-687361de64fa" />


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
