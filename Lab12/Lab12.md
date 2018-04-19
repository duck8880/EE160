# EE160 Lab 11: Those Dreaded Pointers 

(Repo of lab notes: <https://github.com/duck8880/EE160>)

(Lab 12 spec: http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab12/lab12.html)

​     

## Notes

- The essence of pointers:

  http://www-ee.eng.hawaii.edu/cgi-local/mklec.cgi?37+2+EE160/S18


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

    ```
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
    ```

- (3 Points). **Using Pointers**

    Write a function, `swap_big()`, which is given two pointers to floats (a, b) and swaps the values in the cells pointed to such that *a <= *b. The prototype for your function is:

    ```c
    void swap_big(float *a, float *b);
    ```

    Your data file, **swapbig.dat**, should show that your function works under all conditions. The file is expected cover the cases of a > b, a < b and a = b.

    Write a driver to allow you to test this function for different pairs of floats when redirected from your data file.  **You should use the swap() function from the previous problem to implement your function.** (I suggest turn off the debugging in swap() function finally.) Run your program using the input redirection command: 

    ```bash
    swapbig < swapbig.dat
    ```

    ​

    Essential files for this program: swap.c, swapbig.c, *the driver*, some *.h files*, swapbig.dat

    ​

- (3 Points). **More Pointers and Functions**

    Write a function, `reorder()`, which is given three pointers to floats and reorders the values pointed to into ascending order (i.e. *a <= *b <= *c). The prototype for this function is:

    ```c
    void reorder(float *a, float *b, float *c);
    ```

    Use your `swap_big()` function from the previous problem to implement reorder(). Your data file, **reorder.dat**, should show that your function works under all conditions. Write a driver to allow you to test this function for different triplets of floats when redirected from your data file. Run your program using the input redirection command: 

    ```bash
    reorder < reorder.dat
    ```

    ​

    Hint: You can be inspired from the [**swaptest.c**](http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab12/swaptest.c) in the first program. We need to call swap_big() three times to obtain the ascending order of three numbers.

    ​

    Essential files for this program: swap.c, swapbig.c, reorder.c, *the driver*, some *.h files*, reorder.dat






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
