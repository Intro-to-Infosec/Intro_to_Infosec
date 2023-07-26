# Assignment - 1
## Markups and Screenshots for solving using DVWA 

### Command Injection -
On Security level - low : command 127.0.0.1; ls worked and showed this 

![low](https://github.com/Intro-to-Infosec/assignment-1-AhemazizSingh/assets/121503197/6a54bccc-bd09-40a0-a103-d00bb75fe39b)

But on medium security it didnt work. Even the command 127.0.0.1 && ls also didnt work so used only '&' to access the files i.e 127.0.0.1 & ls and could use other commands as cat.php like 127.0.0.1 & cat.php

![c](https://github.com/Intro-to-Infosec/assignment-1-AhemazizSingh/assets/121503197/0f251926-4353-4ccb-b8d4-2bbbdee598ae)

### Command Injection(High) -
Used command 127.0.0.1|ls i.e without space to bypass the checks 

### XSS(Reflected) -
On low security used payload <script>alert(1)</script> to redirect but on medium and high security ,script keyword is replaced so can use payload <scr<script>ipt>("You are hacked")</script> 
![xss1](https://github.com/Intro-to-Infosec/assignment-1-AhemazizSingh/assets/121503197/26631637-5206-4d5d-b752-d5c906b888f8)

Can also use this -

![xss](https://github.com/Intro-to-Infosec/assignment-1-AhemazizSingh/assets/121503197/6c503d65-123c-4638-9e97-0d414552acc3)


### XSS(DOM) -
Added this payload to the url </select><img%20src/onerror=alert("hacked")>![xss-dom](https://github.com/Intro-to-Infosec/assignment-1-AhemazizSingh/assets/121503197/6ac50b88-e352-4cc5-ba78-641504e3d31a)


### SQL Injection -
Inspected the page to change the value of any option to '1 or 1=1' (i.e. Always true condition) and got all the names. ![sql](https://github.com/Intro-to-Infosec/assignment-1-AhemazizSingh/assets/121503197/bf09ea80-75af-4cb8-aad5-665401c4637b)
![sql1](https://github.com/Intro-to-Infosec/assignment-1-AhemazizSingh/assets/121503197/3840bb73-ece1-4661-878a-a4a70e729f3c)


### XSS(Stored) - 
First used payload <script>alert(1)</script> but didnt worked. Also capitalizing it <SCRIPT>alert(1)</SCRIPT> didn't work.  So enterded the payload in name column but it had restriction to the lengh so changed it by inspecting.















