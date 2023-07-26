# Writeup for Solving Levels from Microcorruption-
## New Orleans -  
Started by inputting 'test' as password.   
On looking into <create password> - we see it pointing to r15 (2400) and it gets stored in r14  
And in <check_password> first r14 count is cleared then on using step r13 points to same memory as r15;  
then again on stepping r13 is added to r14 which is zero.    
Then the r13 and 2400 in memory and r14(zero byte) are compared.
So the password is aNW[IdY

![New Orleans door](https://github.com/Intro-to-Infosec/Intro_to_Infosec/assets/121503197/875f4f0c-d304-46f8-9b5b-43848284f90a)

## Hanoi-
First on continuing we find that password is 8-16 characters so we input anything in between (eg. randominput) which is not correct.
In Main we see login call so we look into login-
Our goal is to get access granted so for this it compares the hex value

## Cusco-

First we input random password for login between 8-16 characters  
and find that it is stored in 43e0 and 43f0 in memory   
so we reset it and now input hex value which is more than 16 characters and then use step function to unlock the door. 

![Cusco door unlocked](https://github.com/Intro-to-Infosec/Intro_to_Infosec/assets/121503197/27d74ea8-1244-4426-8824-aacd546bcbc3)

