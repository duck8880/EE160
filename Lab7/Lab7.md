# EE160 Lab 7: A mini-mini Project (Homework 2) 

(Repo of lab notes: <https://github.com/duck8880/EE160>)

(Homework 2: <http://www-ee.eng.hawaii.edu/~tep/EE160/S18/Hw/Hw2/hw2.html>)

​     

## Notes

- Common mistakes

  - If you want to test two or more conditions, use ""**&&**"" or "**||**" in **while()** or **if()** statement: 

    ```c
    while(a >= 0 && a <= 10) { ... }
    if (b == 0 || b == 1) { ... }
    ```

  - Pay attention to variable types in expressions: 

     ```c
     int a = 5;
     int b = 2;
     float c;
     c = a / b;				   // c = 2.0 !
     c = (float)a / (float)b;	// c = 2.5
     ```

  - "**=**" and "**==**": 

     ```c
     if (a == 1) { ... }
     // if (a = 1) { ... }	// Wrong!
     if (1 == a) { ... }
     ```

  - Make sure your programs compile and give expected output before submission.

- Useful VI commands to copy, cut paste, etc.

    `v`: enter visual mode;    `h`, `j`, `k`, `l`: move cursor  
    `0`: to the beginning of a line;    `$`: to the end of a line  
    `c`: cut;    `y`: copy;    `p`: paste;    `cc` or `dd`: cut the current line;    `yy`: copy the current line  
    `u`: undo;    `Ctrl`+`r`: redo


​     


## Introduction

- Task: Write a program to find the difference between two dates. 

  Due: **5 Mar 2018 (Monday)**

- Work in teams, and submit only **ONE** set of files per team. **ALL** members of the team should contribute to the homework.

- Write **comments** on your code to describe the **ALGORITHM**. Write **heading comment** in each of your source files: 

  ```c
  /*     file:    the name of the file
         by:      the name of the programmer who wrote this file
         login:   the login id of the programmer who wrote this file
         date:    the date
         team:    your team name
         members: your teammates' names
  */
  ```

- Example program provided by Dr. Dobry is located in: 

  ​	`~ee160/Homework/Hw2/datediff`

  Example output: 

  ```bash
  Enter a start date (dd mm yy) (EOF to quit): 20 2 2018
  Enter an ending date (dd mm yy): 5 3 2018
          From 20  2 2018
          To    5  3 2018
                  there are 13 days
  Enter a start date (dd mm yy) (EOF to quit): [Ctrl-D]
  ```

- Make your program robust (i.e. how well they can tolerate user errors). 

- You can use debugging printf() to show some intermediate value and other information in your program, as well as use the Conditional Compilation (using #ifdef). Turn off the debugging before submission.  



​     

## Tasks

0. Create a new directory (e.g. **EE160/Homework/Hw2**) as your working directory.

   Copy `~ee160/Homework/Hw2/makefile` to your working directory.

1. **Leap Years** (4 Points) (Problem 6 in [section 3.9](http://www-ee.eng.hawaii.edu/~tep/EE160/Book/chap3/section2.1.9.html) of the text).

   - Write a function:

     ```c
     int is_leap(int year);
     ```

     which determines if a given year is a leap year. (A year is a leap year if it is divisible by 400; or if it is divisible by 4 and it is not divisible by 100. )

     Put the code for this function in the file **leap.c** and the prototype for the function in the file **leap.h**.

     Tips: use modular operator **%** to test divisibility.

     ```c
     if (year % 400 == 0) { ... }
     ```

   - Write a **main()** which repeatedly asks the user to enter a year and prints if it is a leap year or not. **The program terminates when the user enters 0 for the year.** Put the code for the driver in the file **driver1.c**.

   - Compile the program with **make** command, which creates executable **driver1**: 

     ```bash
     make driver1
     ```
     Example run: 

     ```bash
     Enter a year: 2018
     2018 is not a leap year.
     Enter a year: 2016
     2016 is a leap year.
     Enter a year: 2000
     2000 is a leap year.
     Enter a year: 1900
     1900 is not a leap year.
     Enter a year: 0
     ```

     ​

2. **Days in a Month** (4 Points)

   - Write a function:

     ```c
     int days_in_month(int month, int year);
     ```

     which is given a month and year and returns the number of days in that month. You should use your **is_leap()** function as needed to determine the number of days in the month (February has an extra day in leap years). 

     Put the code for the function **days_in_month() **in the file **days.c**, and the prototype in the file **days.h**.

     Tips: Check invalid input (e.g. month < 1 or month > 12). The function can return -1 to indicate the invalid input.

   - Write a driver, **main()**, to ask the user to enter the month and year (**use EOF to terminate the program**) and prints the number of days. Put the driver in the file **driver2.c**.

   - Compile the program with **make** command, which creates executable **driver2**: 

     ```bash
     make driver2
     ```

     Example run: 

     ```bash
     Enter a month and a year (mm yy): 1 2018
     There are 31 days
     Enter a month and a year (mm yy): 2 2018
     There are 28 days
     Enter a month and a year (mm yy): 4 2018
     There are 30 days
     Enter a month and a year (mm yy): 2 2016
     There are 29 days
     Enter a month and a year (mm yy): 13 2018
     Invalid input!
     Enter a year and a month: [Ctrl-D]
     ```

3. **Julian Date** (5 Points).

   - Write a function:

     ```c
     int julian_date(int day, int month, int year);
     ```

     This function is given the day, month and year and returns the Julian date. The Julian date is the ordinal day number for that day. For example, 1 Jan is day 1 of any year, 31 Dec is day 365 for any non-leap year and 1 Feb is day 32 for any year. 

     Use your **days_in_month()** function from the previous problem to calculate the Julian date. Put the code for the function **julian_date()** in the file **julian.c**, and the prototype in the file **julian.h**.

     Tips: 

     - Check invalid input (e.g. month < 1 or month > 12, or day > total number of days in the current month). The function can return -1 to indicate the invalid input.
     - Use loop to calculate the sum of the days in the previous months. Then return the sum plus the day in the input.

   - Write a driver, **main()**, which asks the user to enter a month, day, year and prints the Julian date. **Terminate with EOF**. Put the driver in the file **driver3.c**.

   - Compile the program with **make** command, which creates executable **driver3**: 

     ```bash
     make driver3
     ```

     Example run: 

     ```bash
     Enter a day, a month and a year (dd mm yy): 1 1 2018
     The Julian date is: 1
     Enter a day, a month and a year (dd mm yy): 31 12 2018
     The Julian date is: 365
     Enter a day, a month and a year (dd mm yy): 31 12 2016
     The Julian date is: 366
     Enter a day, a month and a year (dd mm yy): 10 2 2018
     The Julian date is: 41
     Enter a day, a month and a year (dd mm yy): 30 2 2018
     Invalid input!
     Enter a day, a month and a year (dd mm yy): [Ctrl-D]
     ```

     ​

4. **Date Difference** (7 Points).

   - Write just one more driver using the functions you have written so far. The driver is to read a start date and end date and compute the number of days between them. Terminate the program when **EOF** occurs when reading the start date. Implement your algorithm in main() in the file **datediff.c**. 
   - Compile this program with the command, which will create an executable called **datediff**:

     ```bash
     make datediff
     ```

   ​





## Turn in

- Submit **ONE** copy of all of the files for this homework per team all at one time.

  `grade -2s2,ee160 *.c *.h `  
  ` grade -2s2,ee160`  

- **Each member of the team** should send Dr. Dobry a confidential form evaluating the effort of **each member of the team**, **INCLUDING YOURSLEF**, using the ratings shown on the [rating page](http://www-ee.eng.hawaii.edu/~tep/EE160/eval.html) and use the form you copy from ~ee160/eval.  

  The possible ratings include: Excellent, Very Good, Satisfactory, Ordinary, Marginal, Deficient, Unsatisfactory, Superficial, No Show.  

  Include a **description** at the end of the form of what parts of the programs where done by **each member of the team**, including yourself, and an assessment of how teamwork was used to complete this assignment.

  `cp ~ee160/eval .`  
  `vi eval`  
  `elm -s "EE 160 Hw2 Eval" tep < eval`


  



## Tutorial offering from the CoE

<http://web.eng.hawaii.edu/Tutor/intro.html>

## Unix/Linux Command Cheat Sheet

<https://files.fosswire.com/2007/08/fwunixref.pdf>
