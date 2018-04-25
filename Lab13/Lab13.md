# EE160 Lab 13: Arrays 

(Repo of lab notes: <https://github.com/duck8880/EE160>)

(Lab 13 spec: http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab12/lab12.html)

​     

## Notes

- Please finish the Online Course Evaluation:

  [https://eeforms.eng.hawaii.edu](https://eeforms.eng.hawaii.edu/)

  Your response is important for course improvement. Please feel free to write any comments.

- ​

​     

## Programs

- Create a new directory **`EE160/Labs/Lab13`** as your working directory.

    (1 Point). Write the `makefile` yourself. You can copy a makefile from a previous lab and modify it. 

    The commands we will use to compile your programs are:

    ```bash
    make averages
    make water
    ```

- (4 Points). **Exploring Arrays**

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

    Essential files for this program: swap.c, swapbig.c, *the driver for swap_big()*, some *.h files*, swapbig.dat

    ​

- (5 Points). **Using Arrays** - a tiny project.

    Write a function, `reorder()`, which is given three pointers to floats and reorders the values pointed to into ascending order (i.e. *a <= *b <= *c). The prototype for this function is:

    ```c
    void reorder(float *a, float *b, float *c);
    ```

    Use your `swap_big()` function from the previous problem to implement reorder(). Your data file, **reorder.dat**, should show that your function works under all conditions (e.g. "1 2 3", "1 3 2", "2 1 3", "1 1 2", "2 1 2", ...). Write a driver to allow you to test this function for different triplets of floats when redirected from your data file. Run your program using the input redirection command: 

    ```bash
    reorder < reorder.dat
    ```

    ​

    Hint: You can be inspired from the [**swaptest.c**](http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab12/swaptest.c) in the first program. We need to call swap_big() three times to obtain the ascending order of three numbers.

    ​

    Essential files for this program: swap.c, swapbig.c, reorder.c, *the driver for reorder()*, some *.h files*, reorder.dat




## Submission

- Turn in the all of the source files (.c and .h files) you created using:

  `grade -lab13s2,ee160  *.c *.h makefile`  

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
