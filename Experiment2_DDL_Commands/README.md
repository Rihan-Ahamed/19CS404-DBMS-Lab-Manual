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
Write an SQL query to add two new columns, department_id and manager_id, to the table employee with datatype of INTEGER. The manager_id column should have a default value of NULL.

 

 

 

 

For example:

Test	Result
PRAGMA table_info(employee);
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          integer     0                       0
1           salary      number      0                       0
2           department  INTEGER     0                       0
3           manager_id  INTEGER     0           NULL        0

```sql
alter table employee add column department_id INTEGER;
alter table employee add column manager_id INTEGER default NULL;
```

**Output:**

<img width="1220" height="333" alt="image" src="https://github.com/user-attachments/assets/b607764f-747d-4f88-9802-c124c2bcc1d3" />



**Question 2**
---
Insert a student with RollNo 201, Name David Lee, Gender M, Subject Physics, and MARKS 92 into the Student_details table.

For example:

Test	Result
SELECT * FROM Student_details WHERE RollNo = 201;
RollNo      Name        Gender      Subject     MARKS
----------  ----------  ----------  ----------  ----------
201         David Lee   M           Physics     92

```sql
insert into Student_details values (201,"David Lee","M","Physics",92);

```

**Output:**

<img width="1298" height="228" alt="image" src="https://github.com/user-attachments/assets/c3a2d665-089e-4640-83df-6e7a0d92f5f4" />



**Question 3**
---
Insert all products from Discontinued_products into Products.

Table attributes are ProductID, ProductName, Price, Stock

For example:

Test	Result
select * from Products;
ProductID   ProductName     Price       Stock
----------  --------------  ----------  ----------
101         Old Smartphone  199.99      0
102         Vintage Laptop  399.99      10
103         Classic Tablet  149.99      5
                      0                       0

```sql
insert into Products (ProductID,ProductName,Price,Stock)
select ProductID,ProductName,Price,Stock
from Discontinued_products

```

**Output:**
<img width="1184" height="278" alt="image" src="https://github.com/user-attachments/assets/0ff06a8a-f087-47f0-8339-d17e393319be" />




**Question 4**
---
Create a table named Invoices with the following constraints:

InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
DueDate as DATE should be greater than the InvoiceDate.
Amount as REAL should be greater than 0.
For example:

Test	Result
INSERT INTO Invoices (InvoiceID, InvoiceDate)
VALUES (1, '2024-08-08'),(1,'2024-09-08');
Error: UNIQUE constraint failed: Invoices.InvoiceID


```sql
create table Invoices (
InvoiceID INTEGER primary key,
InvoiceDate DATE,
DueDate Date check(DueDate>InvoiceDate),
Amount REAL check(Amount>0)
);
```

**Output:**

<img width="1199" height="240" alt="image" src="https://github.com/user-attachments/assets/8fee4250-82bd-42f2-9ef7-4f2febc09f5b" />




**Question 5**
---
Create a table named Shipments with the following constraints:
ShipmentID as INTEGER should be the primary key.
ShipmentDate as DATE.
SupplierID as INTEGER should be a foreign key referencing Suppliers(SupplierID).
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).
For example:

Test	Result
INSERT INTO Shipments (ShipmentID, ShipmentDate, SupplierID, OrderID) VALUES (2, '2024-08-03', 99, 1);
Error: FOREIGN KEY constraint failed

```sql

create table Shipments(
ShipmentID INTEGER primary key,
ShipmentDate DATE,
SupplierID INTEGER,
OrderID INTEGER,
foreign key (SupplierID) references Suppliers(SupplierID),
foreign key (OrderID) references Orders(OrderID)
);

```

**Output:**

<img width="1220" height="248" alt="image" src="https://github.com/user-attachments/assets/b0f9b73e-da8a-4ea1-8a17-34504cc20848" />



**Question 6**
---
Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should set NULL on updates and deletes.
item_desc and rate should not accept NULL.
For example:

Test	Result
INSERT INTO item VALUES("ITM5","Charlie Gold",700,"COM4");
UPDATE company SET com_id='COM5' WHERE com_id='COM4';
SELECT * FROM item;
item_id     item_desc     rate        icom_id
----------  ------------  ----------  ----------
ITM5        Charlie Gold  700



```sql
create table item (
item_id text primary key,
item_desc text not null,
rate integer not null,
icom_id text(4),
foreign key (icom_id) references company(com_id)
on update set null
on delete set null
);
```

**Output:**

<img width="1240" height="348" alt="image" src="https://github.com/user-attachments/assets/4398bef7-d752-4a33-bb74-033061dfe3f0" />



**Question 7**
---
Create a table named Attendance with the following constraints:
AttendanceID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
AttendanceDate as DATE.
Status as TEXT should be one of 'Present', 'Absent', 'Leave'.
For example:

Test	Result
INSERT INTO Attendance (AttendanceID, EmployeeID, AttendanceDate, Status) VALUES (1, 1, '2024-08-01', 'Present');
SELECT * FROM Attendance;
AttendanceID  EmployeeID  AttendanceDate  Status
------------  ----------  --------------  ----------
1             1           2024-08-01      Present


```sql
create table Attendance (
AttendanceID integer primary key,
EmployeeID integer,
AttendanceDate DATE,
Status text check(Status in("Present","Absent","Leave")),
foreign key (EmployeeID) references Employees(EmployeeID));
```

**Output:**

<img width="1203" height="276" alt="image" src="https://github.com/user-attachments/assets/cbb3bf6f-86da-4bc0-8b3f-415fe3dccc2a" />




**Question 8**
---
Create a table named Locations with the following columns:

LocationID as INTEGER
LocationName as TEXT
Address as TEXT
For example:

Test	Result
pragma table_info('Locations');
cid       name             type        notnull     dflt_value  pk
--------  ---------------  ----------  ----------  ----------  ----------
0         LocationID       INTEGER     0                       0
1         LocationName     TEXT        0                       0
2         Address          TEXT        0                       0

```sql
create table Locations (
LocationID INTEGER,
LocationName TEXT,
Address TEXT);

```

**Output:**

<img width="1327" height="397" alt="image" src="https://github.com/user-attachments/assets/16394144-dc5e-472e-b7d3-edd957c1b7dc" />




**Question 9**
---
Write an SQL query to add two new columns, designation and net_salary, to the table Companies. The designation column should have a data type of varchar(50), and the net_salary column should have a data type of number.

 

 

For example:

Test	Result
pragma table_info('Companies');
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          int         0                       0
1           name        varchar(50  0                       0
2           address     text        0                       0
3           email       varchar(50  0                       0
4           phone       varchar(10  0                       0
5           designatio  varchar(50  0                       0
6           net_salary  number      0                       0

```sql
alter table Companies add column designation varchar(50);
alter table Companies add column net_salary number;
```

**Output:**

<img width="1242" height="404" alt="image" src="https://github.com/user-attachments/assets/6828c7ad-5869-4659-9405-da487f1baac6" />




**Question 10**
---
In the Products table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

ProductID   Name              Category    Price       Stock
----------  ---------------   ----------  ----------  ----------
106         Fitness Tracker   Wearables
107         Laptop            Electronics  999.99      50
108         Wireless Earbuds  Accessories              100
 

For example:

Test	Result
SELECT * FROM Products;
ProductID   Name             Category    Price       Stock
----------  ---------------  ----------  ----------  ----------
106         Fitness Tracker  Wearables
107         Laptop           Electronic  999.99      50
108         Wireless Earbud  Accessorie              100


```sql
insert into Products values (106,"Fitness Tracker","Wearables", null,null );
insert into Products values (107."Laptop","Electronics",999.99,50);
insert into Products values (108,"Wireless Earbud","Accessorie",null,100);
```

**Output:**


<img width="1217" height="238" alt="image" src="https://github.com/user-attachments/assets/729c07a2-9c68-47ba-a386-97bb0542460f" />




## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
