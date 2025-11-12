# Experiment 7: PL/SQL – Variables, Control Structures and Loops

## AIM
To write and execute simple PL/SQL programs using variables, loops, and conditional statements.


## THEORY

PL/SQL, which stands for Procedural Language extensions to the Structured Query Language (SQL). It is a combination of SQL along with the procedural features of programming languages.

**Syntax:**
```sql
DECLARE 
   <declarations section> 
BEGIN 
   <executable command(s)>
EXCEPTION 
   <exception handling> 
END;
```

### Basic Components of PL/SQL Block:
- DECLARE: Section to declare variables and constants.
- BEGIN: The execution section that contains PL/SQL statements.
- EXCEPTION: Handles errors or exceptions that occur in the program.
- END: Marks the end of the PL/SQL block.

# PL/SQL Programs – Steps and Expected Output

## 1. Write a PL/SQL program to find the Greatest of Two Numbers

### Steps:
- Declare two numeric variables and initialize them.
- Use an `IF` statement to compare the values.
- Display the greater number using `DBMS_OUTPUT.PUT_LINE`.

**Expected Output:**  
Greater number is: 80
## code

<img width="863" height="400" alt="image" src="https://github.com/user-attachments/assets/3aaf25b2-5c42-4dae-8e61-854fa3a31e19" />

## output
<img width="384" height="131" alt="image" src="https://github.com/user-attachments/assets/e0605c8e-a2d7-4966-bccd-2e4906f8e808" />

---

## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

### Steps:
- Declare a variable `n` and assign a value (e.g., 10).
- Initialize a `sum` variable to 0.
- Use a `WHILE` loop to iterate from 1 to `n`, adding each number to the sum.
- Display the result using `DBMS_OUTPUT.PUT_LINE`.

**Expected Output:**  
Sum of first 10 natural numbers is: 55
## code

<img width="889" height="365" alt="image" src="https://github.com/user-attachments/assets/eef5d49c-a61a-468e-8fe7-25f251b153d3" />

## output
<img width="430" height="142" alt="image" src="https://github.com/user-attachments/assets/dc852605-7d6c-448c-9edd-f29219af08f5" />

---

## 3. Write a PL/SQL program to generate Fibonacci series

### Steps:
- Declare the variable `n` to indicate how many terms to generate.
- Initialize the first two Fibonacci numbers (0 and 1).
- Use a loop to generate the next terms using the formula `c = a + b`.
- Print each term in the series.

**Expected Output:**  
n = 7  
Fibonacci sequence: 0, 1, 1, 2, 3, 5, 8
## code

<img width="781" height="486" alt="image" src="https://github.com/user-attachments/assets/639d8acf-8b9e-4275-9995-fa8f1c6c7e20" />

## output

<img width="269" height="186" alt="image" src="https://github.com/user-attachments/assets/b19349f6-7166-40fc-b796-f42db774c40f" />

---

## 4. Write a PL/SQL Program to display the number in Reverse Order

### Steps:
- Declare a variable `n` and assign a value (e.g., 1535).
- Use a loop to extract each digit using modulo and reverse the number.
- Display the reversed number.

**Expected Output:**  
n = 1535  
Reversed number is 5351

## code
<img width="774" height="390" alt="image" src="https://github.com/user-attachments/assets/0c7c679d-b17a-4fb9-b6d1-425f58724944" />

## output

<img width="357" height="186" alt="image" src="https://github.com/user-attachments/assets/bdf5bf64-865e-4434-859a-776bea845956" />

---

## 5. Write a PL/SQL program to find the largest of three numbers

### Steps:
- Declare three numeric variables `a`, `b`, and `c`.
- Use nested `IF-ELSIF-ELSE` conditions to find the largest among the three.
- Display the largest number.

**Expected Output:**  
a = 10, b = 9, c = 15  
Largest of three number is 15

## code

<img width="778" height="406" alt="image" src="https://github.com/user-attachments/assets/fe726450-a70a-4043-b3e3-baac8e38adc4" />

## output

<img width="397" height="144" alt="image" src="https://github.com/user-attachments/assets/4b2fd244-4f4f-437d-a465-50d1c0014d91" />

## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.


