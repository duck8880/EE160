# EE160 Lab 1: Getting Familiar with wiliki
(Repo of lab notes: <https://github.com/duck8880/EE160>)



## TA

  Jianqiu "Chris" Cao (jianqiuc@hawaii.edu)

## Lab time and location

  - Section 2: Thursdays at 7:30-10:15a, POST 214  
  - Office hours:  
    Wednesdays at 10:30-11:30a, POST 214  
    Thursdays at 10:15-11:15a, POST 214

## Note

- Lab 1 is individual work.
- You can use either your laptops or the PCs in the lab. We have 22 PCs in the lab.
- Use Wiliki account. Go to HOLM 250 if you have problem.
- Attend every lab. If you have to miss a lab, contact the TA before lab for making up.
- Sign risk form at <http://tinyurl.com/uhmee-riskform>
- Join EE160 course in Piazza: <https://piazza.com/hawaii/spring2018/ee160>

## Self Introduction

  Name, Major, Year  
  Send me an email with your introduction and a face picture attached  



## Lab 1

(<http://www-ee.eng.hawaii.edu/~tep/EE160/Labs/Lab1/>)

- Login to Wiliki account using **PuTTY** (for Windows)  

  Host Name: `wiliki.eng.hawaii.edu`, Port: `22`,   
  User name and password: `Wiliki account`

- Set up environment (for new users to use csh)

  `cd`  
  `cp ~ee160/dotprofile_csh .profile`  
  `logout`  
  log back in to wiliki  
  `cp ~ee160/dotcshrc .cshrc`  
  `source .cshrc`  
  `test160`  
  `mkdir EE160`  

- Explore Unix

  - Navigating in the Unix file system  
    `pwd`, `cd`, `ls`, `cat`, `more`
  - Managing files and directories  
    `mkdir`, `cp`, `mv`, `rm`
  - Communicating with others  
    `w`, `who`  

- Explore text editor: **vi**  (Do it at the end of the lab)

  `vimtutor`

- Explore email

  - Your email address on wiliki: `your_user_name@wiliki.eng.hawaii.edu`  
    TA's email address on wiliki: `jianqiuc@wiliki.eng.hawaii.edu`
  
  - Delete **.forward** in your home directory first  
    `cd`  
    `rm .forward`  

  - Send an email to three of your classmates

  - **Send an email to your TA telling him the names of the three classmates**  




## Homework 0

(<http://www-ee.eng.hawaii.edu/~tep/EE160/S18/Hw/hw0.html>)

- Complete the questionnaire at the following website, and write down your result.

  <http://www-ee.eng.hawaii.edu/~tep/ILS/ils.html> 

- Fill out the file "**info**"

  `cd`  
  `cd EE160`  
  `cp ~ee160/info .`  
  `vi info`  

- Useful vi commands

  `a` or `Insert` key: Enter **insert** mode  
  `Esc` key: Quit **insert** mode  
  `:w`: Save changes to current file  
  `:q!`: Quit vi without saving  
  `:wq`: Save changes and quit  

- **Email the file "info" to Dr. Tep Dobry**

  `elm`  
  `elm -s "info for ee160" tep < info `   




## Lab Deadlines

- 5% Bonus for complete lab assignments turned in by the end of the scheduled lab session.
- No Penalty for complete lab assignments turned in before the beginning of the next lab session.
- 10% Penalty for complete lab assignments turned in before the beginning of the lab session 2 weeks after the scheduled lab session.
- 50% penalty for lab assignments after that.
- Homework 0 is due at the end of the lab 1 session



## Tutorial offering from the CoE

<http://web.eng.hawaii.edu/Tutor/intro.html>

## Unix/Linux Command Cheat Sheet

<https://files.fosswire.com/2007/08/fwunixref.pdf>

## Get access to wiliki off campus using UH VPN

<http://www.hawaii.edu/askus/819>
