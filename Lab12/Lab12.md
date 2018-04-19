# EE160 Lab 11: Those Dreaded Pointers 

(Repo of lab notes: <https://github.com/duck8880/EE160>)

(Lab 12 spec: http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab12/lab12.html)

​     

## Notes

- Data types: Define variables of higher range to represent data with larger value or higher precision

  - int: -2,147,483,648 to 2,147,483,647
  - float: 1.2E-38 to 3.4E+38(6 decimal places)
  - double: 2.3E-308 to 1.7E+308(15 decimal places)
- This lab may not be as easy as you thought. Even if your algorithm is correct, you may not get the reasonable result. This is due to the limitations on numeric data types. Take advantage of your debugging skills to fix the problems.


​     

## Programs

- Create a new directory **`EE160/Labs/Lab12`** as your working directory.

    (1 Point). Write the `makefile` yourself. You can copy a makefile from a previous lab and modify it. 

    The commands we will use to compile your programs are:

    ```bash
    make swap
    make swapbig
    make reorder
    ```

    (1 Point). Create your own data files that verify that your functions work correctly under all conditions.

    ```bash
    swapbig < swapbig.dat
    reorder < reorder.dat
    ```

- (2 Points). **Exploring Pointers**

    Copy the files [**swap.c**](http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab12/swap.c) and [**swaptest.c**](http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab12/swaptest.c) to your directory. Create the appropriate header file, **swap.h**, for the function defined in **swap.c**. (You can copy the three files from `~ee160/Labs/Lab12`). Compile this program using your makefile with the command:

    ```bash
    make swap
    ```

    Run the program and observe the output. On a piece of paper, draw the picture showing the trace of the code and state what the memory addresses are for the three variables, a, b, and c. **You will turn in this paper to the TA before leaving the lab.**

                                  a             b             c
                            +----------+  +----------+  +----------+
        Initial Values:     |    2.5   |  |    5.9   |  |   12.3   |
                            +----------+  +----------+  +----------+
                      Addr:  0x1055b28c    0x1055b288
                                  ^             ^
                                  |             |
                            +-----+----+  +-----+----+
                            |0x1055b28c|  |0x1055b288|
                            +----------+  +----------+
                                  x             y
        
                                  a             b             c
                            +----------+  +----------+  +----------+
    After the 1st swap:     |    2.5   |  |    5.9   |  |   12.3   |
                            +----------+  +----------+  +----------+
                      Addr:  0x1055b28c    0x1055b288    0x1055b284
                                                ^             ^
                                                |             |
                                          +-----+----+  +-----+----+
                                          |0x1055b288|  |0x1055b284|
                                          +----------+  +----------+
                                                x             y

    After the 2nd swap:      ......


    After the 3rd swap:      ......





## Submission

- Turn in the all of the source files (.c and .h files) you created using:

  `grade -lab12s2,ee160  *.c *.h *.dat  makefile`  

  Verify your submission using:

  `grade -lab12s2,ee160`  


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
