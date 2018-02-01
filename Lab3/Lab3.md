# EE160 Lab 2: Arithmetic Expressions and Program I/O

(Repo of lab notes: <https://github.com/duck8880/EE160>)

(Lab assignment: <http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab3/lab3.html>)

  ​


## Programs

- Create a new directory called **Lab3** in your **EE160/Labs** directory.

  `cd EE160/Labs`  
  `mkdir Lab3`  
  `cd Lab3`

- (2 Points) Copy your repaired version of the **gravity.c** file from your **Lab2** directory. Modify the program to read the **time** from the user as a **float** value and compute the **distance** and **speed**.

  `cp ../Lab2/gravity.c .`  
  `vi gravity.c`  
  `cc gravity.c`  
  `./a.out`

  example input and output:  

  ``` bash
  Enter the time: 10
  An object falling 1600 feet in 10.00 seconds is traveling 320.00 ft/sec
  ```

- (2 Points) Fix the bugs in [seconds.c](http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab3/seconds.c): Given an **integer** number of **seconds**, compute how many **hours**, **minutes** (within an hour) and **seconds** (within a minute) this corresponds to.

  `vi seconds.c`  
  `cc seconds.c`  
  `/.a.out`  

  example input and output:  

  ```bash
  Enter the number of seconds: 3775
  there are 1 hours, 2 minutes, 55 seconds
  ```

- (2 Points) Modify the program [cars.c](http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab3/cars.c) to remove unnecessary parentheses in the arithmetic expressions while maintaining the meaning of the program.  

  Example input and output:  

  ```bash
  Enter sticker price: 100000
  Sticker price:                                  100000.00
  Price after 12.0% discount:                     88000.00
  Taxes (luxury and sales):                        9469.60
  Total cost:                                     97469.60
  ```

- (2 Points) Write a program **gas.c** to compute some statistics on gas. 

  Input: the **number of gallons used**, the **number of miles** since the last fill up. 

  Output: the **number of gallons**, the **cost per gallon** ($3.12), the **cost of the fill-up**, **cost per mile**, and **miles per gallon** for the fill-up.

  Example input and output:  

  ```bash
  Enter the number of gallons used: 10
  Enter the number of miles: 300
  The number of gallons used: 10.00
  The cost per gallon: 3.12
  The cost of the fill-up: 31.20
  Cost per mile: 0.10
  miles per gallon: 30.00
  ```

- (2 Points) Write a program **temperature.c** to convert temperatures in degrees Fahrenheit to degrees Celsius. 

  *C = (F - 32) * 5 / 9*.

  Example input and output:  

  ```bash
  Enter the temperature in degrees Fahrenheit: 80
  Temperature in degrees Celsius is: 26.67
  ```




## Turn in

- Use the "**grade**" command to turn in these five programs, and verify

  `grade -lab3s2,ee160 gravity.c seconds.c cars.c gas.c temperature.c`  
  ` grade -lab3s2,ee160`  




## Notes

- Try to eliminate all the warnings:  

  ```c
  #include <stdio.h>
  int main(){
    int a;
    scanf("%d", &a);
  }
  ```

  ​


## Tutorial offering from the CoE

<http://web.eng.hawaii.edu/Tutor/intro.html>

## Unix/Linux Command Cheat Sheet

<https://files.fosswire.com/2007/08/fwunixref.pdf>


