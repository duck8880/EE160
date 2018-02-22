# EE160 Lab 6: If Statements and Separate Compilation 

(Repo of lab notes: <https://github.com/duck8880/EE160>)

(Lab assignment: <http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab6/lab6.html>)

  ​

## Notes

- Make sure your programs compile and eliminate all the warnings.. 

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

- Check your grades:

   `mygrades ee160s2`

- If you want to review the topics covered by the lecture so far, see the [summary](http://www-ee.eng.hawaii.edu/cgi-local/mklec.cgi?18+3+EE160/S18). 

  Ask me if you have any question about the midterm.

- Useful VI commands to copy, cut paste, etc.

    `v`: enter visual mode;    `h`, `j`, `k`, `l`: move cursor  
    `0`: to the beginning of a line;    `$`: to the end of a line  
    `c`: cut;    `y`: copy;    `p`: paste;    `cc` or `dd`: cut the current line;    `yy`: copy the current line
    `u`: undo;    `Ctrl`+`r`: redo

  ​

## Programs

- Create a new directory called **Lab6** in your **EE160/Labs** directory. Work in this directory.

- (3 Points). Do problem 4 in [section 2.9](http://www-ee.eng.hawaii.edu/~tep/EE160/Book/chap2/section2.1.9.html) of the text.

   

  - ​





## Turn in

- Use the "**grade**" command to turn in these five programs, and verify

  `grade -lab5s2,ee160 sum.c avg.c weight.c temptbl.c account.c `  
  ` grade -lab5s2,ee160`  


  ​



## Tutorial offering from the CoE

<http://web.eng.hawaii.edu/Tutor/intro.html>

## Unix/Linux Command Cheat Sheet

<https://files.fosswire.com/2007/08/fwunixref.pdf>
