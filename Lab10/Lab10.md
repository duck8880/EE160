# EE160 Lab 10: More Loops 

(Repo of lab notes: <https://github.com/duck8880/EE160>)

(Lab 8 spec: <http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab10/lab10.html>)

​     

## Notes

- Common mistakes

  - **Properly use ""&&"" or "||" in the condition in the if() statement:** 

    The following two blocks of code with if statements are equivalent: 

    ```c
    if (A > 100 || A <= B) { 
      // Invalid input of grading scale A 
    } else {
      // Valid A
    }
    ```
    or
    ```c
    if (A <= 100 && A > B) { 
      // Valid input of grading scale A 
    } else {
      // Invalid A
    }
    ```

    To give the converse of a statement, we must change "&&" to "||" or vise versa.

    ​

  - **We don't have to write the `if (a <= 0)` in the following code :** 

    ```c
    if (a > 0) {
        // do something
    } else if (a <= 0) {
        // do another thing
    }
    ```
    Just write like this:

    ```c
    if (a > 0) {
        // do something
    } else {
        // do another thing
    }
    ```

    ​

  - **\#include only .h files in your .c files. Never \#include .c files.**

    E.g. we have driver.c, grader.c and grader.h in our program.

    In grader.c:

    ```c
    #include "driver.h"
    char assign_grade(int score) {
        //...
    }
    ```

    In grader.h:

    ```c
    char assign_grade(int score);
    ```

    In driver.c:

    ```c
    #include <stdio.h>
    #include "driver.h"
    //...
    grade = assign_grade(score);
    ```

    ​

  - **Makefile**

    ```makefile
    # target to make all programs for Lab 9
    all: mygrader mygrader2 countgrades

    # Problem 1 - grader programs
    #       complete the dependency and action lines for your filenames
    mygrader: driver.o grader.o
            cc  -o mygrader driver.o grader.o

    mygrader2: driver2.o grader2.o
            cc  -o mygrader2 driver2.o grader2.o

    # Problem 2 - grade counter
    countgrades: countgrades.o
            cc -o countgrades countgrades.o

    # source file dependencies
    #       add target lines showing dependencies for your .o files
    driver.o:

    grader.o:

    driver2.o:

    grader2.o:

    countgrades.o:

    # utility targets

    clean:
            rm -f *.o

    real_clean: clean
            rm -f mygrader mygrader1 countgrades
    ```

  ​

- While loop vs for loop

  The while loop:
  ```c
  i = 1;
  while (i <= n)
  { 
          printf("%d\n", i);
          i++;
  }
  ```

  is equivalent to the following for loop:
  ```c
  for (i = 1; i <= n; i++)
  {
          printf("%d\n", i);
  }
  ```

  Note that the 1st expression in the for statement can be blank sometimes.

  ​

- Be free to ask me if you have any question about the midterm 2.

​     

## Tasks

- Create a new directory **`EE160/Labs/Lab10`** as your working directory.

- (6 Points). **Exploring the "for" and "while" statements.**

  Note: all the .c files in this problem are available at `~ee160/Labs/Lab10/`. We can copy them into your working directory beforehand.

  - Compile and run the counting program, [**counters.c**](http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab10/counters.c). Copy it into a new file **counters2.c**, and rewrite the program so that it uses only for loops rather than while loops.

    Sample run:
    ```bash
    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    10
    9
    8
    7
    6
    5
    4
    3
    2
    1
    5
    8
    11
    14
    15
    12
    9
    6
    ```

  - Compile and run the [**avg.c**](http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab10/avg.c) . Rewrite it to use a while loop rather than a for.

    Sample run:
    ```bash
    10
    20
    35
    Average of 3 values is 21.666667.
    ```


  - Compile and run the program [questions.c](http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab10/questions.c). It reads in a line from the user and determines whether it is a yes or no based on the first character on the line. Rewrite it using "while" loops instead of for loops.

    [questions2.c](http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab10/questions2.c) is the same program, but with printf statements for debugging. You can also work with questions2.c, but delete all of its debugging statements.

    Note: There are some small issues in the program. To get rid of them, do the following things:

    1. Create the header file [tfdef.h ](http://www-ee.eng.hawaii.edu/~tep/EE160/Code/Lecture/Stock/tfdef.h) in the working directory.
    2. Add `#include <ctype.h>` at the beginning of the .c file. The function `tolower()` is defined there.
    3. Add the function prototype `int yesOrNo(void);` in the .c file before the main() function.

    Sample run:

    ```
    Don't you just love this class? Y
    YES!  We knew it.
    ```

    ```
    Don't you just love this class? y123
    YES!  We knew it.
    ```

    ```
    Don't you just love this class? N123
    NO?  Come on, you know you love this class.
    ```

    ```
    Don't you just love this class? 123n
    Please answer with a YES or NO: Y123
    YES!  We knew it.
    ```

  ​

- (4 Points). **Exploring leaving loops early**.

  Compile and run the program [averager.c](http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab10/averager.c). It is supposed to repeatedly read a number, then reads that number of values and prints their average.

  Example run for regular input:

  ```bash
  5
  10 20 30 40 50
  Average of 5 values is 30.00
  7
  15 20 40 50 60 40 50
  Average of 7 values is 39.29
  ```

  Fix the programs so that:  

  1. If it receives garbage input instead of integers for the expected number of values, it prints the following error message and quits.

     Example run:

     ```bash
     some garbage input
     Error!  Can't read number of expected values.
     ```

     Hint: The `scanf()` function will return 0 if it reads no valid value. You can use `break;` to quit a while loop.

  2. If it receives garbage input instead of integers when it is trying to read one of the values it should be averaging but some valid values are read before that, It prints the following error message, print the average of the valid values and quits.

     Example run: (The "50" is #0, so the "whatever" should be #2.)

     ```bash
     6
     50 70 whatever 40 60
     Error!  Can't read expected value #2.
     Average of 2 values is 60.00
     ```

     Hint: If it receives garbage while reading values in the inner loop, you need to quit the inner loop first and then quit the outer loop. You can detect the abnormal termination of the inner by comparing the `count` with the `expected` after it quits.






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
