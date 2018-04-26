# EE160 Lab 13: Arrays 

(Repo of lab notes: <https://github.com/duck8880/EE160>)

(Lab 13 spec: http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab13/lab13.html)

​     

## Notes

- Please finish the Online Course Evaluation:

  [https://eeforms.eng.hawaii.edu](https://eeforms.eng.hawaii.edu/)

  Your response is important for course improvement. Please feel free to write any comments.

- The final deadline for any lab work you would like graded is **Friday, 4 May at 11:59 pm**.

- Tip: You can use FileZilla to upload files to or download files from Wiliki.

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

    Compile and run the program [averages.c](http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab13/averages.c). Its input and output was supposed to look like the following.

    ```bash
    10 20 30 30 40 50
    Average of the 6 values read is: 30.000000
    There are 2 values equal to the average.
    The values greater than the average:
    40
    50
    The values less than the average:
    10
    20
    ```

    0. Break this code up into .c separate source files with related functions together in a file, and provide the appropriate .h files. Document the files with meaningful comments.

    1. Make it compute the average correctly. 

       Hint: This can be done by rewriting the **tableAverage()** function.

    2. Make it determine the number of elements equal to the average correctly. 

       Hint: This can be done by rewriting the **tableMatchingElements()** function.

    3. Make it print the values greater than or less than the average. The program currently uses tablePrint(), but this prints all elements. 

       Hint: A reasonable approach is to make two new functions **tablePrintIfLarger()** and **tablePrintIfSmaller()** that are like tablePrint(), except that they only print the appropriate subset of array elements.

- (5 Points). **Using Arrays** - a tiny project (**Water Meter Reader**).

    The new digital meters measure water consumed in each household by incrementing a counter for each gallon of water used. Each hour, the controller stores the counter in memory (without resetting it). Every night at midnight the controller sends a file consisting of a time stamp and the counter reading for each hour of the day to the BWS computer over the fiber. A sample of the file is in [day1](http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab13/day1).

    Write a program to process these files. The program should read the data file and compute **the water usage for each hour of the day**, **the average hourly usage for the day**, and **the time of the highest hourly usage**.

    ​

    The .c files, .h files. data file and a sample executable can be copied from `~ee160/Code.lect/Water`.

    Run the sample executable by:

    ```
    water < day1
    ```


    The output is:

    ```
                     0:00   3
                     1:00   151
                     2:00   4
                     3:00   2
                     4:00   22
                     5:00   36
                     6:00   8
                     7:00   2
                     8:00   3
                     9:00   2
                    10:00   0
                    11:00   1
                    12:00   2
                    13:00   3
                    14:00   1
                    15:00   5
                    16:00   6
                    17:00   18
                    18:00   5
                    19:00   4
                    20:00   31
                    21:00   14
                    22:00   2
                    23:00   2


    the average usage was 13.625000
    the hi usage was 151 at 1:00
    ```

    ​

    Your task is to complete this program by writing the function **compute_usage()** in a NEW file **meter.c**. The prototype of the function is already in **meter.h**.

    Tips: 

    - The pointer ***hi_idx** is pointing to the array index rather than the highest usage.
    - Pay attention to that what the last array index should be.



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
