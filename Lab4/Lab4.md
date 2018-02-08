# EE160 Lab 4: Functions and Loops

(Repo of lab notes: <https://github.com/duck8880/EE160>)

(Lab assignment: <http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab4/lab4.html>)

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

- Function definition and declaration

  definition - call: 

  ```c
  int func1(int a){
      return a + 1;
  }
  int main(){
      int a = 1;
      int b;
      b = func1(a);
  }
  ```

  declaration - call - definition: 

  ```c
  int func1(int a);	// function prototype
  int main(){
      int a = 1;
      int b;
      b = func1(a);
  }
  int func1(int a){
      return a + 1;
  }
  ```

- Add comments to the code to document the program.

- You can open multiple windows to login to wiliki. One for editing the source files, and another for running the programs.


  ​

## Programs

- Create a new directory called **Lab4** in your **EE160/Labs** directory.

  `cd EE160/Labs`  
  `mkdir Lab4`  
  `cd Lab4`

  ​

- (2 Points) Fix the bugs in [**countup.c**](http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab4/countup.c), which prints the integers 1 through 20 on separate lines and then stop.

  Fix the bugs in [**countdown.c**](http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab4/countdown.c), which prints the integers 10 down through 1 on separate lines and then print "BLASTOFF".

  `vi countup.c`  
  `cc countup.c`  
  `./a.out`  
  `...`

  example output of **countup.c**:  

  ``` bash
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
  11
  12
  13
  14
  15
  16
  17
  18
  19
  20
  ```
  Example output of **countdown.c**:

  ```bash
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
  BLASTOFF!
  ```

  ​

- (2 Points) Copy your **temperature.c** file from your **Lab3** directory into your **Lab4** directory. Modify the program to compute the conversion from Fahrenheit to Celsius in a function called **tocelsius()**. The prototype for this function is:

  ```c
  float tocelsius(float fahrenheit);
  /*  Given:  a temperature reading in degrees Fahrenheit
      Returns: the temperature in degrees Celsius
  */
  ```

  Keep prompting the user to enter a temperature in Fahrenheit, and print the value in Celsius until the user enters "**-500**".

  ​

  `cp ../Lab3/temperature.c .`  
  `vi temperature.c`  
  `cc temperature.c`  
  `/.a.out`  

  ​

  example input and output:  

  ```bash
  Enter the temperature in degrees Fahrenheit: 80
  temperature in degrees Celsius is: 26.67
  Enter the temperature in degrees Fahrenheit: 0
  temperature in degrees Celsius is: -17.78
  Enter the temperature in degrees Fahrenheit: -500
  ```
  ​

  Tips: Commands in VI to copy, cut paste, etc.:

  `v`: enter visual mode			`h`, `j`, `k`, `l`: move cursor  
  `0`: to the beginning of a line	`$`: to the end of a line  
  `c`: cut		`y`: copy		`p`: paste	`cc` or `dd`: cut the current line		`yy`: copy the current line
  `u`: undo	`Ctrl`+`r`: redo

  ​

- (2 Points) Copy your **temperature.c** file to a file called **temptbl.c**. Add another function to the file:

  ```c
  int temptable(float start, float stop);
  /*  Given: starting and ending temperatures in degrees Fahrenheit
      
      The function prints a table of conversions from degrees
      Fahrenheit to degrees Celsius from start to at most stop
      in five degree F increments, one conversion per line.

      Returns: the number of table lines printed.
  */
  ```

  The function, **temptable()**, should use your function, **tocelsius()**. Modify the driver, **main()**, to prompt the user to enter the start and stop temperatures and print the table, until the user enters the same value for start and stop. 

  Note: Before write any code, write the algorithms for the function **temptable()** and the driver **main()** **IN WORDS** in a text file called **algorithms**(2 points).  Refer to the algorithm description: <http://www-ee.eng.hawaii.edu/~tep/EE160/Notes/Basics/loop_count.html>



  ``vi algorithms``  

  `cp temperature.c temptbl.c`  
  `vi temptbl.c`  
  `cc temptbl.c`  
  `./a.out`


  Example input and output:  

  ```bash
  Enter the start temperature in degrees Fahrenheit: 50
  Enter the stop temperature in degrees Fahrenheit: 82
  Fahrenheit      Celsius
  50.000000       10.000000
  55.000000       12.777778
  60.000000       15.555555
  65.000000       18.333334
  70.000000       21.111111
  75.000000       23.888889
  80.000000       26.666666
  Enter the start temperature in degrees Fahrenheit: 50
  Enter the stop temperature in degrees Fahrenheit: 50  
  ```

  


- (2 Points) Write a program **account.c** to solve problem 15 in [section 3.9](http://ee.hawaii.edu/~tep/EE160/Book/chap3/section2.1.9.html#SECTION0019000000000000000).

  Input: the **initial amount**, annual **interest rate** (e.g. 0.05 for 5%), and **number of years** of compounding.

  Output: the **accumulated value**.

  The program should process user input until the user enters **0** for the **initial amount**.
  
  ​

  Write the algorithms for **calc_acc_amt()** and **main()**, adding them to your **algorithms** file.

  The prototype of **calc_acc_amt()** is:

  ```c
  float calc_acc_amt(float acc_amount, float annual_interest, int years);
  ```


  The equation for calculating the new accumulated value from the accumulated value in last year: 

      *acc_amount = acc_amount + acc_amount * annual_interest*

  ​

  Example input and output:  

  ```bash
  Enter initial amount: 100
  Enter interest rate: 0.05
  Enter number of years: 1
  Accumulated value: 105.000000
  Enter initial amount: 100
  Enter interest rate: 0.05
  Enter number of years: 10
  Accumulated value: 162.889450
  Enter initial amount: 0
  ```

  


## Turn in

- Use the "**grade**" command to turn in these five programs, and verify

  `grade -lab4s2,ee160 algorithms countup.c countdown.c temperature.c temptbl.c account.c`  
  ` grade -lab4s2,ee160`  


  ​



## Tutorial offering from the CoE

<http://web.eng.hawaii.edu/Tutor/intro.html>

## Unix/Linux Command Cheat Sheet

<https://files.fosswire.com/2007/08/fwunixref.pdf>


