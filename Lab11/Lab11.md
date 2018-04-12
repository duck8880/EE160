# EE160 Lab 11: Limitations on Numeric Data Types and Numeric Algorithms 

(Repo of lab notes: <https://github.com/duck8880/EE160>)

(Lab 11 spec: http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab11/lab11.html)

​     

## Notes

- Common mistakes

  - ​
- This lab may not be as easy as you thought. Even if your algorithm is correct, you may not get the reasonable result. This is due to the limitations on numeric data types. Take advantage of your debugging skills to fix the problems.


​     

## Tasks

- Create a new directory **`EE160/Labs/Lab11`** as your working directory.

- (10 Points). **Write a function to evaluate `sin(x)` using the expansion shown below. Use it in a program to find the sine of values read until end of file.**

<a href="https://www.codecogs.com/eqnedit.php?latex=sin(x)&space;=&space;\frac{x^{1}}{1!}&space;-&space;\frac{x^{3}}{3!}&space;&plus;&space;\frac{x^{5}}{5!}&space;-&space;\frac{x^{7}}{7!}&space;&plus;&space;\frac{x^{9}}{9!}&space;-&space;..." target="_blank"><img src="https://latex.codecogs.com/gif.latex?sin(x)&space;=&space;\frac{x^{1}}{1!}&space;-&space;\frac{x^{3}}{3!}&space;&plus;&space;\frac{x^{5}}{5!}&space;-&space;\frac{x^{7}}{7!}&space;&plus;&space;\frac{x^{9}}{9!}&space;-&space;..." title="sin(x) = \frac{x^{1}}{1!} - \frac{x^{3}}{3!} + \frac{x^{5}}{5!} - \frac{x^{7}}{7!} + \frac{x^{9}}{9!} - ..." /></a>


​







## Submission

- Turn in the all of the source files (.c and .h files) you created using:

  `grade -lab10s2,ee160  *.c *.h`  

  Verify your submission using:

  `grade -lab10s2,ee160`  


   ​

## Useful VI commands to copy, cut, paste, etc.

  `v`: enter visual mode;    `h`, `j`, `k`, `l`: move cursor  
  `0`: to the beginning of a line;    `$`: to the end of a line  
  `c`: cut;    `y`: copy;    `p`: paste;    `cc` or `dd`: cut the current line;    `yy`: copy the current line  
  `u`: undo;    `Ctrl`+`r`: redo

## Tutorial offering from the CoE

<http://web.eng.hawaii.edu/Tutor/intro.html>

## Unix/Linux Command Cheat Sheet

<https://files.fosswire.com/2007/08/fwunixref.pdf>
