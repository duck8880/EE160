# EE160 Lab 5: More Functions and Loops

(Repo of lab notes: <https://github.com/duck8880/EE160>)

(Lab assignment: <http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab5/lab5.html>)

  ​

## Notes

- Eliminate all the warnings, or there will be deduction on your points. 

  Example:  

  ```c
  #include <stdio.h>
  int main(){
    int a;
    float b = 1.0;
    
    printf("Enter a: ");
    scanf("%d", &a);
    printf("a = %d, b = %f\n", a, b);
  }
  ```

- Write your algorithms in the comments in your .c files. There may be also deduction if you didn't describe your algorithms properly.

- Refer to [Lab 4 notes](https://github.com/duck8880/EE160/blob/master/Lab4/Lab4.md) for Unix and VI commands.

  ​

## Programs

- Create a new directory called **Lab5** in your **EE160/Labs** directory. Work in this directory.

- (2 Points). Complete the program, [**sum.c**](http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab5/sum.c), by translating the algorithm given there into C. 

  - __Input__: a set of numbers; __Output__: the sum of the numbers. 

  - You should terminate the input with the end-of-file character(`[Ctrl-D]`).

    Example code for detecting the EOF:
  ```c
  #include <stdio.h>
  int main() {
      //...
      int flag;
      flag = scanf("%d", &number);
      //...
      while( flag != EOF ){
          //...
          flag = scanf("%d", &number);
         //...
      }
      //...
  }
  ```

  Example input and output:
  ```bash
  Enter a number: 10
  Enter a number: 20
  Enter a number: 30
  Enter a number: [Ctrl-D]
  The sum of the numbers is: 60
  ```

- (2 Points). Copy your **sum.c** file into **avg.c**. Modify the algorithm and then the code to print the average of the input instead of the sum.

  Example input and output:

  ```bash
  Enter an integer value: 10
  Enter an integer value: 20
  Enter an integer value: 35
  Enter an integer value: [control-D]
  The average of 3 input values is 21.67
  ```

  Tips: Define the values as integer and define the average as float. Count the number of input value in the while loop. 

- (2 Points). Copy the **avg.c** program into **weight.c** and modify it to read and compute a weighted average.

  *weighted average = Σ value / Σ weight*

  Example input and output:

  ```bash
  Enter a weight/value pair: 20 90
  Enter a weight/value pair: 30 80
  Enter a weight/value pair: 50 60
  Enter a weight/value pair: [control-D]
  The weighted average of 3 input values is 72.000000
  ```

  Tips: 

  - Define two variables to calculate the sum of value and the sum of weight.
  - Read two value with one scanf() function: `flag = scanf("%d %d", &weight, &value);`

- (2 Points). Copy your **temptbl.c** file from your **Lab4** directory into your **Lab5** directory. New temptable() function is like: 

  ```c
  int temptable(float start, float stop, float step);
  /*  Given: starting and ending temperatures in degrees Fahrenheit
             and a step size.
      
      The function prints a table of conversions from degrees
      Fahrenheit to degrees Celsius from start to at most stop
      in "step" degree F increments, one conversion per line.

      Returns: the number of table lines printed.
    */
  ```

  New program needs to implement the followings (difference from the program in lab 4):

  - Step specified by argument in the **temptable()** function. 
  - Check the arguments to get rid of invalid inputs in the **temptable()** function:
    - If start < stop, then print from low to high. If start > stop, then print from high to low. 
    - if -0.001 < step < 0.001, print error message "No table--step smaller than 0.001!" rather than the table.
    - if step < 0, then step = -step.
  - Print the number of temperatures in the table.
  - Keep ask user for input until get `[Ctrl-D]`.

  Example input and output: 

  ```bash
  Enter start, stop and step: 32 64 4
  Fahrenheit      Celsius
  32.00           0.00
  36.00           2.22
  40.00           4.44
  44.00           6.67
  48.00           8.89
  52.00           11.11
  56.00           13.33
  60.00           15.56
  64.00           17.78
  Computed 9 tempertures
  Enter start, stop and step: 42 32 5
  Fahrenheit      Celsius
  42.00           5.56
  37.00           2.78
  32.00           0.00
  Computed 3 tempertures
  Enter start, stop and step: 42 32 -5
  Fahrenheit      Celsius
  42.00           5.56
  37.00           2.78
  32.00           0.00
  Computed 3 tempertures
  Enter start, stop and step: 42 32 0.0001
  No table--step smaller than 0.001!
  Computed 0 tempertures
  Enter start, stop and step: 42 42 5
  Fahrenheit      Celsius
  42.00           5.56
  Computed 1 tempertures
  Enter start, stop and step:[Ctrl-D]
  ```

- (2 Points) Modify the program **account.c** in **Lab4** to solve **problem 16** in [section 3.9](http://ee.hawaii.edu/~tep/EE160/Book/chap3/section2.1.9.html#SECTION0019000000000000000). Copy your account.c file from your **Lab4** directory into your **Lab5** directory. 

  Requirement: 

  - Input: the **initial amount**, annual **interest rate** (e.g. 0.05 for 5%), 

  - Prompt for either **annually (1), monthly (2) or daily (3) compounding**, and input the **number of years, months or days** correspondingly.

  - Output: the **accumulated value**.

  - Terminate if user input the EOF for **initial amount**.

  - Use simple macros to avoid any "magic numbers" in your code, e.g.:

    ```c
    #define ANNUALLY	1
    #define MONTHLY		2
    #define DAILY		3
    ```

  Hint: the trick is how you get the values you pass to the function calc_acc_amt(). Think about what the MEANING of the parameters are.

  Example input and output:

  ```bash
  Enter initial amount: 100
  Enter annual interest rate: 0.05
  Compound interest annually(1), monthly(2) or daily(3)? 1
  Enter number of years: 1
  Accumulated value: 105.000000
  Enter initial amount: 100
  Enter annual interest rate: 0.05
  Compound interest annually(1), monthly(2) or daily(3)? 2
  Enter number of months: 12
  Accumulated value: 105.116188
  Enter initial amount: 100
  Enter annual interest rate: 0.05
  Compound interest annually(1), monthly(2) or daily(3)? 3
  Enter number of days: 365
  Accumulated value: 105.126816
  Enter initial amount: [Ctrl-D]
  ```

  ​






## Turn in

- Use the "**grade**" command to turn in these five programs, and verify

  `grade -lab5s2,ee160 sum.c avg.c weight.c temptbl.c account.c `  
  ` grade -lab5s2,ee160`  


  ​



## Tutorial offering from the CoE

<http://web.eng.hawaii.edu/Tutor/intro.html>

## Unix/Linux Command Cheat Sheet

<https://files.fosswire.com/2007/08/fwunixref.pdf>
