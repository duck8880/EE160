# EE160 Lab 9: More Character Processing and Debugging Programs 

(Repo of lab notes: <https://github.com/duck8880/EE160>)

(Lab 8 spec: <http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab9/lab9.html>)




​     

## Tasks

- (1 Points). Create a new directory **`EE160/Labs/Lab9`** as your working directory.

  Copy `~ee160/Labs/Lab9/makefile` to your working directory.

  ```makefile

  # target to make all programs for Lab 9
  all: mygrader mygrader2 countgrades

  # Problem 1 - grader programs
  #       complete the dependency and action lines for your filenames
  mygrader:	# add .o files here
          cc  -o mygrader		# add .o files here

  mygrader2:	# add .o files here
          cc  -o mygrader2	# add .o files here

  # Problem 2 - grade counter
  countgrades: countgrades.o
          cc -o countgrades countgrades.o

  # source file dependencies
  #       add target lines showing dependencies for your .o files


  # utility targets

  clean:
          rm -f *.o

  real_clean: clean
          rm -f mygrader mygrader1 countgrades

  ```

  ​

- (6 Points). **Exploring decision-making statements.** 

  1. Compile and run the program found in [grader.c](http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab9/grader.c). This program is intended to read test scores and print out a grade. (Note that it currently assigns all students a grade of '?')

     Tasks:

     - Break this program up into three files, one for the **driver**, and one for the **function** with it's associated **.h file**. (e.g. driver.c, grader.c and grader.h)

       Tip: You can use `:w filename` or `:wq filename` for "save as..."in the editor VI.

     - Add comments to your files to properly document the program showing the algorithm, and properly documenting the function and its prototype. 

     - Compile this program using **make** to verify it compiles and runs at this point. The name of the executable should be **mygrader**. Note that you need to eliminate the warnings in the original program.

       Add necessary content to the **makefile**. (You can ignore the error message for mygrader2 and countgrades now.) Refer to the makefile in Lab8: <https://github.com/duck8880/EE160/blob/master/Lab8/Lab8.md>

     Sample run:

     ```bash
     50
     50: ?
     70
     70: ?
     [Ctrl-D]
     ```

  2. Update the body of the **assign_grade()** function so that it returns an appropriate letter grade: 'A' for a score between 90 and 100, 'B' for a score between 80 and 89, 'C' for a score between 70 and 79, 'D' for a score between 60 and 69, and an 'F' for a score between 0 and 59. An out-of-range score (less than 0 or over 100) should result in a '?' being returned for the grade. 

     When testing the program, instead of entering the data manually, you need to try to redirect data in the file [mygrader.dat](http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab9/mygrader.dat) (also located on wiliki `~ee160/Labs/Lab9/mygrader.dat`) to the user input by using the command:

     ​	`mygrader < mygrader.dat`

     The lecture note on Input Redirection: 

     ​	<http://www-ee.eng.hawaii.edu/~tep/EE160/Notes/Basics/redirect.html>

     Sample run:

     ```bash
     95: A
     85: B
     80: B
     75: C
     70: C
     68: D
     50: F
     104: ?
     -10: ?
     ```

     Hint: There are two ways to do this: one using an else-if, the other as a set of simple if statements, each having a return statement in the then-part of the statement, which is as follows.

     ```c
     if (condition1)
         return 'A';
     if (condition2)
         return 'B';
     //...
     return '?';
     ```

  3. Now extend the mygrader program to print an error message for bad grades, rather than just a question mark.

     **Hint**: We just need to change main() function in the driver.

     Sample run:

     ```bash
     95: A
     85: B
     80: B
     75: C
     70: C
     68: D
     50: F
     104: illegal score
     -10: illegal score
     ```

  4. **Copy your files for this program to new file names** and extend this program to read in the grading scale. (Note: The new executable should be **mygrader2**. Don't destroy the source files for mygrader)

     That is the first 4 input values are taken as the minimum grade for an A, for a B, for a C, and for a D. Here's an example using the traditional grading scale with input from the file [mygrader2.dat](http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab9/mygrader2.dat) (also available on wiliki: `~ee160/Labs/Lab9/mygrader.dat`).

     Add content to the **makefile**, and compile the source files into executable **mygrader2** using **make**.

     **Hint**: It helps to change the assign_grade() function to take the different items of the grading scale as parameters.

     The sample run for the input in mygrader2.dat is the same as the previous part.

  5. In addition, extend the mygrader2 program to verify that the grading scale is reasonable. The rule is: 

     - the minimum score for an A must be larger than the minimum score for a B, and the minimum score for a B must be larger than the minimum score for a C, and so on. 
     - The minimum score for an A must also be no larger than 100 and the minimum score for a D must be no smaller than a 0. 

     If the grading scale is not reasonable, you print a message before reading and processing any of the scores. 

     Here is an example of an illegal grading scale and the resulting program output.

     ```bash
     90 95 70 60
     invalid grading scale
     ```

     **Hint**: It helps to write a function that determines whether the grading scale is valid.

  6. Extend the program to print the total number of students who pass or fail, where **passing is a grade of 'C' or better** and **failing is a 'D' or 'F'**.

     Sample run:

     ```bash
     95: A
     85: B
     80: B
     75: C
     70: C
     68: D
     50: F
     104: illegal score
     -10: illegal score
     Passing scores: 5
     Failing scores: 2
     Illegal scores: 2
     ```

- (3 Points). **Exploring how to debug decision statements.**

  Compile and run the program found in [countgrades.c](http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab9/countgrades.c). This program is supposed to read a series of input characters representing grades (e.g., an 'a' or 'A' represents an A, a 'b' or 'B' represents a 'B', and so on) and print counts of each grade. 

  Tasks:

  - Modified the code so that it works correctly. Here is some sample input and the output it is supposed to produce:

  ```bash
  abcDFEGH
  DdFFEEaA
  [Ctrl-D]
  Grade counts:
    A's: 3
    B's: 1
    C's: 1
    D's: 3
    F's: 3
    Other grades: 5
  ```

  - Add debugging printf() in your code, and turn off the debugging finally before submission:
    - Put a print statement at the beginning of the loop (before the switch) that prints each character that's read. 
    - Add one statement for each case in the switch (as well as the default) that prints the value of the counter after it is updated. 
  - Comment the code in your file to show the algorithm. 

  Hint: Don't count the newline character (**'\n'**).




## Submission

- Turn in the all of the source files (.c and .h files) you created using:

  `grade -lab9s2,ee160  *.c *.h makefile`  

  Verify your submission using:

  `grade -lab9s2,ee160`  


   

## Useful VI commands to copy, cut, paste, etc.

  `v`: enter visual mode;    `h`, `j`, `k`, `l`: move cursor  
  `0`: to the beginning of a line;    `$`: to the end of a line  
  `c`: cut;    `y`: copy;    `p`: paste;    `cc` or `dd`: cut the current line;    `yy`: copy the current line  
  `u`: undo;    `Ctrl`+`r`: redo

## Tutorial offering from the CoE

<http://web.eng.hawaii.edu/Tutor/intro.html>

## Unix/Linux Command Cheat Sheet

<https://files.fosswire.com/2007/08/fwunixref.pdf>
