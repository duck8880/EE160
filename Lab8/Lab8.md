# EE160 Lab 8: Links, Makefiles and Character Processing 

(Repo of lab notes: <https://github.com/duck8880/EE160>)

(Lab 8 spec: <http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab8/lab8.html>)

​     

## Notes

- Common mistakes

  - Properly use ""**&&**"" or "**||**" in the condition in **while()** or **if()** statement: 

    ```c
    while(a >= 0 && a <= 10) { ... }
    if (b == 0 || b == 1) { ... }
    ```

  - We don't have to write the `if (a <= 0)` in the following code : 

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

- Symbolic link

   A symbolic link is similar to a "shortcut" in Windows. It's a file that contains a reference to another file or directory.

   We can create a symbolic link in the current directory to a file in another directory using:

   ```bash
   ln -f -s /inst/ee/ee160/ee160/Code.lect/Roman/roman.c .
   ```

   We can remove a symbolic link roman.c using:

   ```bash
   unlink roman.c
   ```

- Makefile

  ```makefile
  ROMAN = /inst/ee/ee160/ee160/Code.lect/Roman
  CHAP4 = /inst/ee/ee160/ee160/Code.text/Chap4

  roman: driver.o roman.o romanutil.o
          cc driver.o roman.o romanutil.o -o roman

  driver.o: roman.h

  roman.o: roman.h romanutil.h

  romanutil.o: roman.h romanutil.h tfdef.h chrutil.h

  links:
          ln -f -s $(ROMAN)/roman.c .
          ln -f -s $(ROMAN)/roman.h .
          ln -f -s $(ROMAN)/romanutil.c .
          ln -f -s $(ROMAN)/romanutil.h .
          ln -f -s $(ROMAN)/driver.c .
          ln -f -s $(CHAP4)/chrutil.h .
          ln -f -s $(CHAP4)/tfdef.h .

  clean:
          rm *.o

  real_clean: clean
          rm roman
  ```

- You can see more details about **char** and **ASCII** code in the following lecture notes.
 
  <http://www-ee.eng.hawaii.edu/cgi-local/mklec.cgi?23+1+EE160/S18>  
  <http://www-ee.eng.hawaii.edu/~tep/EE160/Notes/Chars/char_rep.html>


​     

## Tasks

- (5 Points). Create a new directory **`EE160/Labs/Lab8`** as your working directory.

  Copy `~ee160/Code.lect/Roman/makefile` to your working directory.

  Run `make links` to create symbolic links to the .c and .h files.

  Tasks: 

  - We would like the program to be tolerant of white space (spaces and tabs), and still provide the result if all of the other characters are valid roman digits.
  
  - If the user enters invalid characters, we would like the function to return 0 as a special value indicating an error instead of a partial result so far.  The driver should **print an error message** when this occurs and let the user try entering another number. 

  Hints: (These hints are the TA's approach, you may find alternative approaches as long as your program works well for the input.)

  - You may modify any of the files that you need to, but you will need to break the link and copy the file for those you want to change. E.g. if you want to modify roman.c, run the following command:

    ```bash
    cp roman.c roman1.c
    unlink roman.c
    mv roman1.c roman.c
    vi roman.c
    ```

  - In **roman.c**, we need to add some code for detecting **spaces**(' '), **tabs**(''\t') in the while loop.

    There may be three situations that the new value of rdigit makes the while loop terminates:
    1. If the *rdigit* is EOF, we return EOF.
    2. If the *rdight* is newline('\n'), which means that all the charaters in the input are valid roman numeral except spaces and tabs, we will return the number.
    3. Otherwise, the *rdight* should be an invalid character, and we need to flush all the following character until the newline character and then return 0. Here is the code for flush the buffer:
    ```c
        while(getchar()!='\n');
    ```

  - In **driver.c**, if the return value of  get_roman() is 0, print an error message.

  Sample run:

  ```bash
  Enter an number in roman numerals(EOF to quit): XI
  The number is 11
  Enter an number in roman numerals(EOF to quit): [Tab]X[Space]I
  The number is 11
  Enter an number in roman numerals(EOF to quit): [Tab]X123
  Invalid input, re-enter an number.
  Enter an number in roman numerals(EOF to quit): [Tab]IX
  The number is 9
  Enter an number in roman numerals(EOF to quit): [Ctrl-D]
  ```

  ​


- (5 Points). Compile and run the program found in [readcmd.c](http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab8/readcmd.c). This program accepts single letter commands as input and simply prints out the command it read. Any blanks in front of the command are ignored, as are any characters after the command.

  Sample run:

  ```bash
  a
  The command is: a
  [Space][Space]a
  The command is: a
  [Space][Space]and this is a long line
  The command is: a
  [Ctrl-D]
  ```

  Tasks: 

  1. Document **readcmd.c** with comments for the algorithm or for the functions.

  2. Copy the program into **myreadcmd.c**, and extend this file to ignores leading **tabs** ('\t') as well as leading **blanks**(' ') (or any combinations of blanks and tabs). 

     Also, extend the program to have either a **semi-colon**(';') or a **newline**('\n') character indicate the end of a command. 

     Sample run:

     ```bash
     a[Space];[Tab]b
     The command is: a
     The command is: b
     [Space]a
     The command is: a
     [Ctrl-D]
     ```

  3. Extend the program to verify that the command is an **upper** or **lower case** letter. It should print an error message if it isn't. Also, verify that the line has a command: if it hits a blank or ; without an intervening command, you should print an error. 
    
    Hint: (These hints are the TA's approach, you may find alternative approaches as long as your program works well for the input.)
     
       There are three situations for the return value of skipBlanks() (cmd):
     
       1. If the "*cmd*" is a upper or lower case letter, then we will print out the letter, and call the `skipOverRestOfCommand()` followed by the `cmd = skipBlanks()`; 
       2. If the "*cmd*" is a delimiter (";" or newline), it means there is missing command before the delimiter, then we need to print an error message, but dont't call `skipOverRestOfCommand()` before calling `cmd = skipBlanks()` for finding the next command; 
       3. Otherwise, the "*cmd*" should be a non-letter charater, then we will print an error, and call the `skipOverRestOfCommand()` followed by the `cmd = skipBlanks()`.

     Sample run:

     ```bash
     a[Space];[Tab]b
     The command is: a
     The command is: b
     [Space]+
     Error: + is not a letter.
     /
     Error: / is not a letter.
     [Enter]
     Error: missing command.
     ;[Tab]b
     Error: missing command.
     The command is: b
     [Ctrl-D]
     ```

     ​




## Submission

- Turn in the all of the source files (.c and .h files) you created using:

  `grade -lab8s2,ee160  *.c *.h`  

  Verify your submission using:

  `grade -lab8s2,ee160`  


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
