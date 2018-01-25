# EE160 Lab 2: Team Organization and Getting started with C

(Repo of lab notes: <https://github.com/duck8880/EE160>)

(Lab assignment: <http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab2/lab2.html>)



## Note

- Sign risk form at <http://tinyurl.com/uhmee-riskform> (**Please sign separately for EE160!**)



## 1. Team Formation

(Team assignments: <http://www-ee.eng.hawaii.edu/~tep/EE160/S18/classlist.html>)

- Team exercise: individual task and team task:

  <http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab2/teamex.html>

- Write up a list of 5 to 10 goals and expectations, and your team name. **Email it to Dr. Dobry, the TA and your team members.**

  ​




## 2. Explore C program creation and compilation.

- Compile, link, and run the C program [welcome.c](http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab2/welcome.c).

  `vi welcome.c`  
  `gcc welcome.c`  
  `./a.out`

- Modify the program in [myname.c](http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab2/myname.c) to print your full name.

- Copy the program that prints your name into a new file named myinfo.c. Extend this program to also print out your complete e-mail address on a separate line after your name.
  `cp myname.c myinfo.c`  
  `vi myinfo.c`  

  Tip: add a new line of "*printf()*" to print out your e-mail address

  `gcc myinfo.c`  
  `./a.out`

- Enter the [pay0.c](http://www-ee.eng.hawaii.edu/~tep/EE160/Code/Textbook/Chap2/pay0.c) program, fix the bugs and get it working. Change it to compute the pay for working 32 hours at a pay rate of $9.75

- Copy gravity.c into your directory, fix the bugs. Compile and run the program.

  `cp ~ee160/Labs/Lab2/gravity.c .`  
  `vi gravity.c`  
  `gcc gravity.c`  
  `./a.out`  

  ​


## More practice with Unix

- In your EE160 directory, create a directory **Labs**

  `mkdir Labs`

- Move all five programs into **Labs**

  `mv gravity.c myinfo.c myname.c pay0.c welcome.c Labs`

- Make a new directory Lab2 inside Labs, and then move all of the files into **Lab2**

  `cd Labs`  
  `mkdir Lab2`  
  `mv *.* Lab2`

- Use the "**grade**" command to turn in these five programs, and verify

  `grade -lab2s2,ee160 welcome.c myname.c myinfo.c pay0.c gravity.c`  
  ` grade -lab2s2,ee160`

  ​

## Lab Deadlines

- 5% Bonus for complete lab assignments turned in by the end of the scheduled lab session.
- No Penalty for complete lab assignments turned in before the beginning of the next lab session.
- 10% Penalty for complete lab assignments turned in before the beginning of the lab session 2 weeks after the scheduled lab session.
- 50% penalty for lab assignments after that.  

  ​



## Tutorial offering from the CoE

<http://web.eng.hawaii.edu/Tutor/intro.html>

## Unix/Linux Command Cheat Sheet

<https://files.fosswire.com/2007/08/fwunixref.pdf>


