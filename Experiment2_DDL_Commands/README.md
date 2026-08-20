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
-- Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should cascade updates and deletes.
item_desc and rate should not accept NULL.

```sql
-- CREATE TABLE item (
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
<img width="803" height="306" alt="image" src="https://github.com/user-attachments/assets/770f295e-4387-4228-998f-a98e66f20820" />


**Question 2**
---
--Write a SQL query to Add a new column State as text in the Student_details table.

Sample table: Student_details

 cid              name             type   notnull     dflt_value  pk
---------------  ---------------  -----  ----------  ----------  ----------
0                RollNo           int    0                       1
1                Name             VARCH  1                       0
2                Gender           TEXT   1                       0
3                Subject          VARCH  0                       0
4                MARKS            INT (  0                       0
```sql
--ALTER TABLE Student_details
ADD COLUMN State TEXT;
```

**Output:**
<img width="1183" height="332" alt="image" src="https://github.com/user-attachments/assets/8048d09d-3d54-4dc2-a7b9-2a68511560bd" />


**Question 3**
---
--Insert the following products into the Products table:

Name        Category     Price       Stock
----------  -----------  ----------  ----------
Smartphone  Electronics  800         150
Headphones  Accessories  200         300

```sql
--INSERT INTO Products(Name,Category,Price,Stock)
VALUES
('Smartphone','Electronics',800,150),
('Headphones','Accessories',200,300);
```

**Output:**
<img width="931" height="337" alt="image" src="https://github.com/user-attachments/assets/8c32d5f3-b10d-4135-a1cc-6d320d7f3b1e" />


**Question 4**
Create a new table named contacts with the following specifications: contact_id as INTEGER and primary key. first_name as TEXT and not NULL. last_name as TEXT and not NULL. email as TEXT. phone as TEXT and not NULL with a check constraint to ensure the length of phone is at least 10 characters.
```
CREATE TABLE contacts (
contact_id INT PRIMARY KEY,
first_name TEXT  NOT NULL,
last_name TEXT NOT NULL,
email TEXT,
phone TEXT  NOT NULL,
CHECK (LENGTH(phone)>=10)
);
```
**Output:**

![image](https://github.com/user-attachments/assets/4232e1e8-adc2-4bcc-aecc-6cb871978988)

**Question 5**
---Write a SQL Query to add an attribute designation in the employee table with the data type VARCHAR(50).
--

```sql
-- ALTER TABLE employee
ADD designation varchar(50)

```

**Output:**
<img width="880" height="251" alt="image" src="https://github.com/user-attachments/assets/9b607124-454e-46a4-b4ab-83f2ad029520" />


**Question 6**
---
--Create a table named Reviews with the following columns:

ReviewID as INTEGER
ProductID as INTEGER
Rating as REAL
ReviewText as TEXT

```sql
--CREATE TABLE Reviews(
ReviewID INTEGER,
ProductID INTEGER,
Rating REAL,
ReviewText TEXT
)
```

**Output:**
<img width="706" height="342" alt="image" src="https://github.com/user-attachments/assets/a7d7fc5c-7155-4a56-a850-ac871eab9cd2" />


**Question 7**
---
--Insert a book with ISBN 978-1234567890, Title Data Science Essentials, Author Jane Doe, Publisher TechBooks, and Year 2024 into the Books table.

```sql
--INSERT INTO Books(ISBN,Title,Author,Publisher,Year)
VALUES ( '978-1234567890','Data Science Essentials','Jane Doe','TechBooks',2024)
```

**Output:**
<img width="776" height="227" alt="image" src="https://github.com/user-attachments/assets/92d95661-c7d9-44e5-8ef4-f77cec0cac07" />


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
<img width="947" height="245" alt="image" src="https://github.com/user-attachments/assets/867b523e-e2f1-4bb9-89b8-1453f2583181" />


**Question 9**
---
-- Insert the below data into the Student_details table, allowing the Subject and MARKS columns to take their default values.

RollNo      Name          Gender      
----------  ------------  ----------  
204         Samuel Black  M          

Note: The Subject and MARKS columns will use their default values.

```sql
--INSERT INTO Student_details(RollNo,Name,Gender)
VALUES(204,'Samuel Black','M')
```

**Output:**
<img width="1171" height="291" alt="image" src="https://github.com/user-attachments/assets/369cafe8-187f-4aac-a7c7-8e645b0e20e2" />


**Question 10**
---
--
Write a SQL query to modify the Student_details table by adding a new column Email of type VARCHAR(50) and updating the column MARKS to have a default value of 0.
```
ALTER TABLE  Student_details ADD COLUMN Email VARCHAR(50);
ALTER TABLE  Student_details ADD COLUMN MARKS DEFAULT '0';
```
**Output:**

![image](https://github.com/user-attachments/assets/a2ad517d-78c6-4489-9474-ae83f64e32ce)


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
