# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
--
What is the total number of medications prescribed for each patient?

Sample tablePrescriptions Table
For example:

Result
PatientID   TotalMedications
----------  ----------------
1           1
2           1
3           1
4           1
5           1
6           1
7           1
8           1
9           1
10          1

```sql
select PatientID ,count(Medication) as TotalMedications
from Prescriptions group by PatientID;
```

**Output:**

<img width="813" height="842" alt="image" src="https://github.com/user-attachments/assets/d765b885-64f8-490b-aecd-9e7277cb54df" />


**Question 2**
---
How many medical records are there for each patient?

Sample table:MedicalRecords Table
For example:

Result
PatientID   TotalRecords
----------  ------------
4           4
5           1
6           1
7           1
8           1
10          2


```sql
select PatientID, count(*) as TotalRecords from MedicalRecords
group by PatientID;
```

**Output:**

<img width="786" height="761" alt="image" src="https://github.com/user-attachments/assets/3de76697-10ec-4f05-a420-422268635c43" />


**Question 3**
---
How many prescriptions were written by each doctor?

Sample tablePrescriptions Table
Result
DoctorID    TotalPrescriptions
----------  ------------------
1           1
2           1
3           1
4           1
5           1
6           1
7           1
8           1
9           1
10          1
```sql
select DoctorID, count(*) as TotalPrescriptions
from Prescriptions
group by DoctorID;
```

**Output:**

<img width="905" height="836" alt="image" src="https://github.com/user-attachments/assets/5500cf06-86e9-483a-b7dc-715b214ba5d4" />


**Question 4**
---
Write a SQL query to Calculate the average email length (in characters) for people who lives in Mumbai city

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT   
city        TEXT
email       TEXT
phone       INTEGER
For example:

Result
avg_email_length_below_30
-------------------------
14.0


```sql
select avg(length(email)) as avg_email_length_below_30 from customer where city="Mumbai";
```

**Output:**

<img width="983" height="395" alt="image" src="https://github.com/user-attachments/assets/4f871963-1144-4979-aa3f-eb9cc3998145" />


**Question 5**
---
Write a SQL query to calculate the total number of working hours of all employees

Sample table: employee1

For example:

Result
Total working hours
-------------------
111


```sql
select sum(workhour) as "Total working hours" from employee1;
```

**Output:**

<img width="704" height="406" alt="image" src="https://github.com/user-attachments/assets/6381c826-fb60-4f36-aa23-6c5efba57482" />


**Question 6**
---
Write a SQL query to find the total amount of fruits with a unit type of 'LB'.

Note: Inventory attribute contains amount of fruits

Table: fruits

name        type
----------  ----------
id          INTEGER
name        TEXT
unit        TEXT
inventory   INTEGER
price       REAL
 

For example:

Result
total
----------
225


```sql
select sum(inventory) as total from fruits
where unit='LB';
```

**Output:**

<img width="546" height="390" alt="image" src="https://github.com/user-attachments/assets/540b30ec-154e-4714-8f3c-5c02ffaefedc" />


**Question 7**
---
Write a SQL query to find the total number of unique cities in the customer table?

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT
city        TEXT
email       TEXT
phone       INTEGER
For example:

Result
unique_cities
-------------
10


```sql
select count(distinct city) as unique_cities from customer;
```

**Output:**

<img width="500" height="407" alt="image" src="https://github.com/user-attachments/assets/5b1d0265-7170-4602-9b61-bebc7a8d6e56" />


**Question 8**
---
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the total work hours for each date, and excludes dates where the total work hour sum is not greater than 40.

Sample table: employee1

For example:

Result
jdate       SUM(workhour)
----------  -------------
2004.0      46
2006.0      46

```sql
select jdate,SUM(workhour) from employee1
group by jdate
having
sum(workhour)>40;
```

**Output:**

<img width="789" height="481" alt="image" src="https://github.com/user-attachments/assets/fe8609b5-eecd-4395-965f-6b1c3a9a9b6e" />


**Question 9**
---
Write the SQL query that achieves the grouping of data by age intervals using the expression (age/5)5, calculates the total salary sum for each group, and excludes groups where the total salary sum is not greater than 5000.

Sample table: customer1



```sql
select (age/5)*5 as age_group ,SUM(salary) from customer1 
group by
(age/5)*5
having
sum(salary)>5000;
```

**Output:**
<img width="746" height="369" alt="image" src="https://github.com/user-attachments/assets/fe9fb79f-0f53-469b-8545-6ab106e9cf1e" />



**Question 10**
---
Write the SQL query that achieves the grouping of data by city, calculates the total income for each city, and includes only those cities where the total income sum is greater than 200,000.

Sample table: employee

```sql
select city, sum(income) as Income from employee group by city having sum(income)>200000;
```

**Output:**

<img width="683" height="609" alt="image" src="https://github.com/user-attachments/assets/85dcb71c-5543-493a-a80c-4591b3a2422e" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
