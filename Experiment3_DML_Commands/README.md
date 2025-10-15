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

--
Write a SQL statement to Update the reorder level to 20 where the quantity in stock is less than 10 and product category is 'Snacks' in the products table.

Products table

---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id

```sql
update Products
set reorder_lvl=20
where quantity <10
and category='Snacks';
```

**Output:**

<img width="1200" height="567" alt="image" src="https://github.com/user-attachments/assets/841af05e-f0bf-42ae-b729-6df234e88c9c" />


**Question 2**
---
Write a SQL statement to Change the supplier name to 'A1 Suppliers' where the supplier ID is 8 in the suppliers table.

Table info

suppliers(supplier_id,supplier_name,contact_person,phone_number,email,address)

For example:

Test	Result
select changes();
changes()
----------
1


```sql
update suppliers
set supplier_name="A1 Suppliers"
where supplier_id=8;
```

**Output:**

<img width="1224" height="404" alt="image" src="https://github.com/user-attachments/assets/109c89d5-37f9-4bdc-84f8-4a819135060a" />


**Question 3**
---
Write a SQL statement to change the first_name column of employees table with 'John' for those employees whose department_id is 80 and gets a commission_pct below 0.35.

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
update Employees 
set first_name="John"
where department_id=80;
```

**Output:**

<img width="1201" height="563" alt="image" src="https://github.com/user-attachments/assets/9dc96818-f584-4618-8ee4-55de22a39b6e" />


**Question 4**
---
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
update Products
set sell_price=sell_price*1.15
where quantity<50
and supplier_id=10;
```

**Output:**

<img width="1210" height="496" alt="image" src="https://github.com/user-attachments/assets/3f3fdf05-b37a-441d-a743-3d25b9fe50d5" />


**Question 5**
---
Write a SQL query to Delete All Doctors with a NULL Specialization

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization
For example:

Test	Result
SELECT * FROM doctors;
doctor_id   first_name  last_name   specialization
----------  ----------  ----------  --------------
1           John        Smith       Cardiology
2           Emily       Johnson     Orthopedics
3           Michael     Brown       Pediatrics
4           Febin       Jones
doctor_id   first_name  last_name   specialization
----------  ----------  ----------  --------------
1           John        Smith       Cardiology
2           Emily       Johnson     Orthopedics
3           Michael     Brown       Pediatrics
```sql
delete from Doctors
where specialization is NULL;
```

**Output:**
<img width="1213" height="898" alt="image" src="https://github.com/user-attachments/assets/4f203a86-9179-4961-b125-7e7249b0a989" />


**Question 6**
---
Write a SQL query to Delete a Specific Surgery whose ID is 3 or surgeon ID is 4.

Sample table: Surgeries

```sql
delete from surgeries
where surgery_id =3
or surgery_id=4;
```

**Output:**

<img width="1188" height="913" alt="image" src="https://github.com/user-attachments/assets/346ba36b-ddfd-4c50-b3ed-20491df2134d" />


**Question 7**
---
Write a SQL query to Delete All Doctors with a NULL Last Name

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization
For example:

Test	Result
SELECT * FROM doctors;
doctor_id   first_name  last_name   specialization
----------  ----------  ----------  --------------
1           John        Smith       Cardiology
2           Emily       Johnson     Orthopedics
3           Michael     Brown       Pediatrics
4           Febin                   Cardiology
doctor_id   first_name  last_name   specialization
----------  ----------  ----------  --------------
1           John        Smith       Cardiology
2           Emily       Johnson     Orthopedics
3           Michael     Brown       Pediatrics

```sql
delete from Doctors
where last_name is null;
```

**Output:**

<img width="1231" height="718" alt="image" src="https://github.com/user-attachments/assets/7e8d1731-c104-4a20-9c8d-3df10168f54c" />


**Question 8**
---
Write a SQL statement to retrieve city(column name) of all customers from customers table without any repeats.

 

 

For example:

Result
city
----------
Chennai
California
Berlin
Moscow


```sql
select distinct city from customers;
```

**Output:**

<img width="1240" height="560" alt="image" src="https://github.com/user-attachments/assets/d0993ee0-aeb7-4d8d-928a-4d83d88a1951" />


**Question 9**
---
Write a SQL query to evaluate the status of rows in the Calculations table based on whether value1 is positive, negative, or zero.

cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          INTEGER     0                       1
1           value1      REAL        0                       0
2           value2      REAL        0                       0
3           base        INTEGER     0                       0
4           exponent    INTEGER     0                       0
5           number      REAL        0                       0
6           decimal     REAL        0                       0

```sql
select id ,value1, case when value1>0 then "Positive" when value1<0 then "Negative" else "Zero" end as value_status from
Calculations;
```

**Output:**
<img width="1254" height="485" alt="image" src="https://github.com/user-attachments/assets/dccc0781-09cf-466b-859a-1a1f9c58c2be" />


**Question 10**
---
Write a SQL query to identify the top 3 most expensive discounted products. Return product_id, original_price, discount_percentage, and discounted_price.

Sample table: Products

product_id | original_price | discount_percentage

 ------------+----------------+--------------------- 

101 | 50.00 | 0.10 

102 | 150.00 | 0.15 

103 | 200.00 | 0.20 

104 | 300.00 | 0.25

```sql
select  product_id, original_price, discount_percentage, original_price*(1-discount_percentage) as discounted_price from Products
order by original_price*(1-discount_percentage) desc limit 3;
```

**Output:**

<img width="1182" height="362" alt="image" src="https://github.com/user-attachments/assets/72569806-8117-4688-b24d-19d844954e7b" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
