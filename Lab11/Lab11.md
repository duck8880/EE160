# EE160 Lab 11: Limitations on Numeric Data Types and Numeric Algorithms 

(Repo of lab notes: <https://github.com/duck8880/EE160>)

(Lab 11 spec: http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab11/lab11.html)

​     

## Notes

- Data types: Define variables of higher range to represent data with larger value or higher precision

  - int: -2,147,483,648 to 2,147,483,647
  - float: 1.2E-38 to 3.4E+38(6 decimal places)
  - double: 2.3E-308 to 1.7E+308(15 decimal places)
- This lab may not be as easy as you thought. Even if your algorithm is correct, you may not get the reasonable result. This is due to the limitations on numeric data types. Take advantage of your debugging skills to fix the problems.


​     

## Tasks

- Create a new directory **`EE160/Labs/Lab11`** as your working directory.

- (10 Points). **Write a function to evaluate `sin(x)` using the expansion shown below. Use it in a program to find the sine of values read until end of file.**

    <a href="https://www.codecogs.com/eqnedit.php?latex=sin(x)&space;=&space;\frac{x^{1}}{1!}&space;-&space;\frac{x^{3}}{3!}&space;&plus;&space;\frac{x^{5}}{5!}&space;-&space;\frac{x^{7}}{7!}&space;&plus;&space;\frac{x^{9}}{9!}&space;-&space;..." target="_blank"><img src="https://latex.codecogs.com/gif.latex?sin(x)&space;=&space;\frac{x^{1}}{1!}&space;-&space;\frac{x^{3}}{3!}&space;&plus;&space;\frac{x^{5}}{5!}&space;-&space;\frac{x^{7}}{7!}&space;&plus;&space;\frac{x^{9}}{9!}&space;-&space;..." title="sin(x) = \frac{x^{1}}{1!} - \frac{x^{3}}{3!} + \frac{x^{5}}{5!} - \frac{x^{7}}{7!} + \frac{x^{9}}{9!} - ..." /></a>

    - Files and functions
      - trig.c, trig.h : 

        `double Sin(float)`: Computes the sin of an angle (given in radians) using the Taylor series shown. Loop terminates when the results in the current iteration and the last iteration are close enough, i.e. the series is convergent.

      - util.c, util.h: 

        `factorial()`: Computes the factorial of an given value

         `close_enough(double, double)`: Given two doubles and returns true if they are within 0.00005 of each other.

      - exponent.c, exponent.h (from Lab 6 and Hw 6): 

        `pos_power()`

      - driver1.c: 

        `int main()`: Gets user input and display the sin(x) until EOF.

      - makefile: <http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab11/makefile>

        Fill in the missing dependencies and action lines.

    - Tips

      - Use `double` data type when necessary. The powers and factorials can be very large after the first few terms.

      - The data type in function definitions, function prototype and variables as arguments should match each other:

        ```c
        double Sin(float);
        int main() {
            float x;
            double s;
            s = Sin(x);
        }
        double Sin(float x) {
        }
        ```

      - Take the time and trouble to print out debug information in every iteration. If your program falls into infinite loop, you can break the loop by inserting scanf()s in the loop:

        ```c
        int temp;
        while(condition) {
            ...
            scanf("%d", temp);
        }
        ```

      - If your function doesn't work for large *x*, adjust *x* to the range of [0, 2π] using its periodicity. Then your program will work for any angle.

        ![Figure](https://mathbitsnotebook.com/Algebra2/TrigGraphs/unitcircle1N.jpg)

        `sin(2kπ + x) = sin(x)`

    - Values of sin(x)

      sin(0) = 0, sin(1) = 0.841471, sin(1.57) = 1.000000, sin(3.14) = 0.001593, sin(6.28) = -0.003185,

      sin(10) = -0.544021, sin(100) = -0.506366, sin(1000) = 0.826880

      sin(-10) = 0.544021,  sin(-100) = 0.506366



   

## Submission

- Turn in the all of the source files (.c and .h files) you created using:

  `grade -lab11s2,ee160  *.c *.h  makefile`  

  Verify your submission using:

  `grade -lab11s2,ee160`  


   ​

## Useful VI commands to copy, cut, paste, etc.

  `v`: enter visual mode;    `h`, `j`, `k`, `l`: move cursor  
  `0`: to the beginning of a line;    `$`: to the end of a line  
  `c`: cut;    `y`: copy;    `p`: paste;    `cc` or `dd`: cut the current line;    `yy`: copy the current line  
  `u`: undo;    `Ctrl`+`r`: redo
   ​

## Tutorial offering from the CoE

<http://web.eng.hawaii.edu/Tutor/intro.html>
   ​

## Unix/Linux Command Cheat Sheet

<https://files.fosswire.com/2007/08/fwunixref.pdf>
