### Cross-Site Scripting(XSS) is a attack where attacker injects malicious javascript into a trusted website so when another users visit the page the browser runs the script as if like it comes from the script. 
Cross ---> Code from outside source
Site ---> runs inside a trusted site
Scripting --> attackers code runs on the victims browser. 


# 1. Reflected XSS into HTML context with nothing encoded 

### Goal : To perform cross-site scripting attack and call alert function. 

### Ingrediants : Search, Home, view post button are there.

<img width="859" height="599" alt="image" src="https://github.com/user-attachments/assets/41778bbf-a7c7-45b0-9db2-5d71b57c4430" />

<img width="817" height="307" alt="image" src="https://github.com/user-attachments/assets/9932878a-1397-4ccf-a645-bfdde8d4a0ec" />

### Solving : 

- Refelcted xss means when we send a malicious script in the request the server immediately back to the page.
- And the lab says HTML context with nothing encoded we can simple write script like <script>alert(2)</script> and we can solve the lab. 

<img width="1254" height="471" alt="image" src="https://github.com/user-attachments/assets/9544e5bd-2f04-46d6-a307-1a0b966bdd9a" />


# -------------------------------------------------------------------------------


2. Stored XSS into HTML context with nothing encoded.


### Goal :   To perform cross-site scripting attack and submit a comment that calls alert function. 

### Ingrediants : Home, View post. 

<img width="863" height="612" alt="image" src="https://github.com/user-attachments/assets/4dd1e679-173b-4cc8-8a0f-4fb8a2152a58" />



<img width="877" height="230" alt="image" src="https://github.com/user-attachments/assets/10710bc8-359a-46ae-b5b3-24325242bfaf" />


### Solving : 

- Stored XSS means it is saved/stored on the server and later served to other users causing the script to run in thier browser whenever they view the stored content
- Since it says submit a comment that calls alert function. By submitting <script>alert(2)</script> this in comment section we can solve the lab.

<img width="791" height="555" alt="image" src="https://github.com/user-attachments/assets/8b7f3854-483d-4928-a671-d95bd8a77c1e" />


# ------------------------------------------------------------------------------


# 3. DOM XSS in document.write sink using source location.search

<img width="731" height="175" alt="image" src="https://github.com/user-attachments/assets/89f0fe30-ad5d-4473-9a0b-beba35b870da" />

### Goal : To perform cross-site scripting attack and call alert function. It uses DOM based XSS. 

### Ingrediants : Home, Search, View post.  

<img width="799" height="579" alt="image" src="https://github.com/user-attachments/assets/07b7ff8c-03e7-420f-bf9d-875baa581d6a" />

<img width="821" height="337" alt="image" src="https://github.com/user-attachments/assets/3a5782cd-9b27-4f0d-b91c-a03941abe5de" />


### Solving :

- Since we got description that it has document.write in the location.search function script we will search something in the search tag and look the code flow. 

<img width="828" height="235" alt="image" src="https://github.com/user-attachments/assets/e415510a-8a0b-4d8c-b5cf-d79e4535bf15" />

<img width="903" height="423" alt="image" src="https://github.com/user-attachments/assets/d55d858c-2c58-455f-969c-a6ccf7d7cd62" />


- We can see wehen we search it has 2 results inside the DOM if it were only one we may think it is reflected xss which is echoes immediately. Here one one result is used normallt to display the search result and another is used inside the image attribute in the searchTerms variable.
- We can we see it is getting the search string in a query and append to the img src's atrribute  in the document.write function. 
- Here only we have to write out malicious payload and call alert().
- src="/resources/images/tracker.gif?searchTerms=sdadasd" We have to close src attribute and should come out put a new attribute and we can call alert().
- We can write payload like sdadasd" onload="alert() so the first double quote " will close src attribute and last " will close the new attribute we introduced.

<img width="1108" height="354" alt="image" src="https://github.com/user-attachments/assets/6f18c638-49a1-4176-aad2-51c65bc0bf12" />

<img width="778" height="401" alt="image" src="https://github.com/user-attachments/assets/a5ca35c4-3562-4e0b-b416-8e8e10f806be" />


# ------------------------------------------------------------------------------


# 4. DOM XSS in innerHTML sink using source location.search 

<img width="738" height="150" alt="image" src="https://github.com/user-attachments/assets/0bddefd4-2a73-4861-a232-ee74652cfc25" />

### Goal :  To perform cross-site scripting attack and call alert function. It uses DOM based XSS. 

### Ingrediants : Same as above. 

### Solving : 

<img width="937" height="414" alt="image" src="https://github.com/user-attachments/assets/c056749f-25d5-4cf0-bf2e-4792909a3f9f" />

<img width="985" height="271" alt="image" src="https://github.com/user-attachments/assets/807435cd-bd19-405e-b5b4-7e3b6ce39633" />

- Unlike the previous lab we can see only one result is found when we search this is because it is using the innerhtml not the document.write.
- document.write ---> When we reload it replaces the whole page with the new input given.
- innerhtml ----> We can abe to change specific element without replace the entire page.
- We can try to print a alert by <script>alert(1)</script>

<img width="823" height="221" alt="image" src="https://github.com/user-attachments/assets/104ee325-57af-4cb9-bc09-b865d4569794" />

<img width="992" height="479" alt="image" src="https://github.com/user-attachments/assets/a401930f-bfd3-4d0a-b461-540450c2b282" />

- It is injected but not executed. This is because in the innerhtml sink it restrict script tag it is part of it's security.
- Hence we can try to inject a img tag like <img src=1 onerror="alert(1)">

<img width="1103" height="441" alt="image" src="https://github.com/user-attachments/assets/a3667336-7091-4411-b348-6d70a638e233" />

- We can see it is executed.

# ------------------------------------------------------------------------------


# 5. DOM XSS in jQuery anchor href attribute sink using location.search source

<img width="716" height="139" alt="image" src="https://github.com/user-attachments/assets/5b40b526-bbcf-48b6-954d-21044f7f6495" />

### Goal :  To make the alert as document.cookie when we click back button. It is using the Jquery sink. 

### Ingrediants : Home, Submit feedback and view post button. 

<img width="939" height="503" alt="image" src="https://github.com/user-attachments/assets/9cf52bb5-57c0-4b2a-a5d8-f20cacb9e3f4" />

<img width="948" height="425" alt="image" src="https://github.com/user-attachments/assets/f48a7dd8-1350-4b01-8ab0-124d86f9729b" />

### Solving : 

- Lets check the is there any back button the page.

<img width="941" height="424" alt="image" src="https://github.com/user-attachments/assets/f46b6092-657c-4c54-8e5c-c49c6bafb1dd" />

<img width="916" height="480" alt="image" src="https://github.com/user-attachments/assets/8fbcd1f4-7677-484a-855a-f5f21d591681" />

- When we inspect the back button elemet we see that it has a function that taking the query parameter and setting the href tag. So this is the vulnerable area we can exploit this.
- Hence we put javascript:alert(document.cookie) this in the return path as query.
- javascript: It will tells the browser to execute this JavaScript instead of opening a normal page.

<img width="1301" height="449" alt="image" src="https://github.com/user-attachments/assets/8d52d35d-035b-4f68-9954-91b7a9eb9ada" />

Hence by doing this we solve the lab. 


# ------------------------------------------------------------------------------


# 6. DOM XSS in jQuery selector sink using a hashchange event

<img width="754" height="176" alt="image" src="https://github.com/user-attachments/assets/aba587ee-e9ca-49f5-9c68-5a11581f3877" />

### Goal : To deliver an exploit to the victim that calls print().

### Ingrediants : Home, Expliot server and view post button. 

<img width="1067" height="609" alt="image" src="https://github.com/user-attachments/assets/656095c0-e98c-4e3d-b3b9-ea0e303dfd58" />


### Solving : 

<img width="989" height="227" alt="image" src="https://github.com/user-attachments/assets/1806e2f2-debe-4731-8dc8-9c426a0ba6d2" />

- We can see it is using the jquery select libary $() and write as function for hash change as whenever we enter the post title after the # in the url it is scroll to that post and it is only one time if we want to get that again for the same post we have to make a change like add number hit enter and again remove it and hit enter. 

<img width="1008" height="445" alt="image" src="https://github.com/user-attachments/assets/3b975569-4d20-4f81-a12d-a929f029a8ce" />

- We can see since it is using the $() it is also creating the html element in the location.hash

<img width="494" height="164" alt="image" src="https://github.com/user-attachments/assets/e6b31dbf-8f71-462b-9156-22de2612b6a6" />

- Hence anything given inside that is saved in the location.hash

<img width="947" height="457" alt="image" src="https://github.com/user-attachments/assets/0a7fea8c-e155-43a9-80cb-e7fb9d33ac05" />

- By pasting this we can able to print. 

<img width="1251" height="489" alt="image" src="https://github.com/user-attachments/assets/d80ce6eb-22b0-4b29-a420-e892d600043a" />

- Let's paste this in the exploit server so the victim will click on this. 

<img width="1165" height="152" alt="image" src="https://github.com/user-attachments/assets/699bf14c-067d-4df3-a110-be1e53e79c94" />

- Hence by uploading this we can solve the lab. 

# ------------------------------------------------------------------------------


# 7. Reflected XSS into attribute with angle brackets HTML-encoded

<img width="762" height="112" alt="image" src="https://github.com/user-attachments/assets/1dac4c9d-4279-4ba0-a082-e9a5b567d649" />

### Goal : To perform a XSS by injecting an attribute and calls the alert(). 

### Ingrediants : Home, search and view post button. 

<img width="914" height="473" alt="image" src="https://github.com/user-attachments/assets/82946709-c201-4fd2-bb06-824c3ef9463d" />

### Solving :

<img width="1083" height="523" alt="image" src="https://github.com/user-attachments/assets/abca7634-6286-4e19-a04c-a3043e959a8a" />

- Since it is using the reflected xss first thing we have to do is searching an orbitary value in the serach box and see where are all it is used.

<img width="994" height="615" alt="image" src="https://github.com/user-attachments/assets/f711ef27-e9f4-42d1-94ba-6fd1c01a77e8" />

- Since our search value is found inside the input tag in the value attribute we will try to break out the atribute by introducing the onmouseover attribute and call alert

<img width="1150" height="466" alt="image" src="https://github.com/user-attachments/assets/d78b391a-f36c-4eb2-9020-c3186bda45fe" />

- When user hover it we can see the alert funtion.

<img width="905" height="417" alt="image" src="https://github.com/user-attachments/assets/aea841a1-89c1-4148-8d4e-bd8bdedd6423" />

- We can see it is comes out. 

<img width="872" height="130" alt="image" src="https://github.com/user-attachments/assets/1b30e18c-78d8-44e8-8b16-df1258958fcf" />


# ------------------------------------------------------------------------------


# 8. Stored XSS into anchor href attribute with double quotes HTML-encoded 

<img width="764" height="97" alt="image" src="https://github.com/user-attachments/assets/78d7e274-052a-4d96-8503-d7ce36c861bb" />

### Goal :  To submit a commment that call alert() when user name is clicked. 

### Ingrediants : View post, home button. 

<img width="829" height="333" alt="image" src="https://github.com/user-attachments/assets/c775cbaa-b156-4414-a4b9-8f058fd92066" />

### Solving : 

- Lets put a ramdom comment and check how the comment tag works. 

<img width="751" height="543" alt="image" src="https://github.com/user-attachments/assets/4b15c56e-d8b2-4be2-8a6a-d906d7693339" />

- We can see the comment and the name is a hyperlink academy url and append value of our given website in the comment. 

<img width="867" height="603" alt="image" src="https://github.com/user-attachments/assets/28fe3c04-2e57-4031-a584-082d65189179" />

<img width="1056" height="215" alt="image" src="https://github.com/user-attachments/assets/7e1b0bc9-3c24-4606-b2c1-3ba7d2413a75" />

- Also we can see it is collecting the website in the href in <a tag. This is our vulernable spot where we can inject malicious payload that can cause alert. 

<img width="1056" height="215" alt="image" src="https://github.com/user-attachments/assets/e42d2e84-adb0-4451-ad82-499954a384b1" />

- In the href tag the value we will provide need not to be a url link it can be javascript hence we do this and solve the lab. 

<img width="797" height="574" alt="image" src="https://github.com/user-attachments/assets/8bebe0ad-9303-4b24-8a9b-10e926435b59" />


# ------------------------------------------------------------------------------


# 9. Reflected XSS into a JavaScript string with angle brackets HTML encoded

<img width="763" height="145" alt="image" src="https://github.com/user-attachments/assets/0368fb37-034e-4487-b77e-856fea2e6211" />

### Goal : Perform XSS which breaks out of Javascript string and call alert(). 

### Ingrediants : View post, home button. 

<img width="933" height="602" alt="image" src="https://github.com/user-attachments/assets/38f2daab-cdec-4c7e-bd7a-4444be0b5cb9" />

- Since it is using the reflected xss first thing we have to do is searching an orbitary value in the serach box and see where are all it is used.

<img width="1050" height="497" alt="image" src="https://github.com/user-attachments/assets/3289f32f-cfba-462f-ba38-5de5e2094ddd" />

- We will try to inject ' + alert() + '  
  
<img width="1312" height="527" alt="image" src="https://github.com/user-attachments/assets/65d26004-1bbb-4a73-b501-31ae889881ff" />

- It worked it comes out of the string as it take it as the 3 seperate value '' one set and then alert() pop up comes then ''


# ------------------------------------------------------------------------------

# 10. DOM XSS in document.write sink using source location.search inside a select element. 

<img width="780" height="238" alt="image" src="https://github.com/user-attachments/assets/9497ca74-0fd7-40cf-81b6-62759ff7d601" />

### Goal : Perform XSS which breaks out of select element string and call alert().

### Ingredients : View details, check stock, return to list and home button, . 

<img width="1305" height="597" alt="image" src="https://github.com/user-attachments/assets/e07e9fa3-b04b-4fbd-a09d-9bcfccdd0455" />

<img width="1245" height="239" alt="image" src="https://github.com/user-attachments/assets/0ff27f72-5146-4039-ab42-d6ecd876a73c" />


### Solving : 

- We can see it is loading a script which has the function of getting the location.search value from the storeId and writing it. 

<img width="1100" height="262" alt="image" src="https://github.com/user-attachments/assets/ff60b3a6-cc49-4624-887a-ce49b007819e" />

- location.search is sink in JS which is the string from this ?

<img width="1142" height="523" alt="image" src="https://github.com/user-attachments/assets/d7ad721e-3e30-490a-bd0b-50a66f9cd913" />

- Since it uses the storeID we try to give a random value to the store ID and sees where it goes and we can see it is added to the list. 

<img width="1219" height="644" alt="image" src="https://github.com/user-attachments/assets/387a200d-f1c4-4985-8a4e-e519237ff1cc" />

- Now we want to get out of the tag. By doing the following. 

<img width="1295" height="657" alt="image" src="https://github.com/user-attachments/assets/d40b84b2-1c9e-48a5-85b8-1dd3a2d591db" />

- Then we can put our malicious payload and the lab is solved. 

<img width="1174" height="679" alt="image" src="https://github.com/user-attachments/assets/80ec2816-0143-4a02-85f7-12966a633e17" />


# ------------------------------------------------------------------------------


# 11. DOM XSS in AngularJS expression with angle brackets and double quotes HTML-encoded

<img width="750" height="271" alt="image" src="https://github.com/user-attachments/assets/fa2a0730-9e09-481e-a489-d27811e79c19" />

### Goal : To perform XSS that executes Angular JS expressions and calls alert(). 

### Ingredients : Home, Search and view post button. 

<img width="854" height="587" alt="image" src="https://github.com/user-attachments/assets/1b66be4d-876b-48fb-adf3-441aa4b0e7b3" />

### Solving : 

- Since it has the search box we will try to inject our usual payload and see the source code where it is used. 

<img width="818" height="281" alt="image" src="https://github.com/user-attachments/assets/34068522-4aca-4638-9bdb-3f7e2cba29d7" />

- And noticed that it is URL encoding so it is blocking "<" tag its using the angularjs file and out search is placed inside the <ng-app>

<img width="774" height="461" alt="image" src="https://github.com/user-attachments/assets/3b5cec71-1b61-4465-a79c-6fbcaae8cff8" />

<img width="1110" height="405" alt="image" src="https://github.com/user-attachments/assets/a40514fc-f0e7-4065-b4c9-57a7515a9e3a" />

- So it is using the Angular JS so < will be blocked and when we give inside the {{ }} it will be executed even the url is encoded.

<img width="871" height="235" alt="image" src="https://github.com/user-attachments/assets/efa3496e-21eb-427d-a0e5-be08b1aceee1" />

- Before that we need to know what scope is.
- Scope is a bridge which connects JS and the html. So we can call a function from the html like a clicking a button, hovering and it is executed. We can also use a default scope functions in the html and call them. 
- These are the default scope functions. 
$new(),  $destroy(), $watch(),  $watchGroup(), $watchCollection(), $digest(), $apply(), $applyAsync(), $eval(), $evalAsync(), $on(), $emit(), $broadcast()
- Since it is using the AngularJS it will block if we use like example $new.Function('alert()'). Hence we will use this $new.contructor because every function has the contructor 
- So it will be {{$new.contructor('alert()')()}} It will create this alert function and by giving () this it will call the function.

<img width="1098" height="394" alt="image" src="https://github.com/user-attachments/assets/133de5f0-c658-4a41-9035-cb2a840ecdb8" />

- Hence we solve the lab.

# ------------------------------------------------------------------------------

# 12. Reflected DOM XSS

<img width="762" height="171" alt="image" src="https://github.com/user-attachments/assets/97bd2fde-5688-48e1-ae08-71ebfef3040e" />

### Goal : To create an injection that calls the alert(). 

### Ingredients : Same as above. 

### Solving : 

- Since it is using the reflected xss first thing we have to do is searching an orbitary value in the serach box and see where are all it is used.

<img width="1142" height="343" alt="image" src="https://github.com/user-attachments/assets/0afabd9d-8938-4942-bf3b-7e3252ed734e" />

- When we examine the .js file. we can see it is uses the eval function which is very dangerous function because whatever inside it is runs first and executed without the permission. 

<img width="938" height="310" alt="image" src="https://github.com/user-attachments/assets/5d77df9e-9f95-4d94-afe9-e2e90d212cb4" />

- Since our search object is going to that we try to modify the according execute an alert() using the burp suite.

 <img width="833" height="282" alt="image" src="https://github.com/user-attachments/assets/7415c97e-cc0c-4796-9475-b3c4688a5e86" />

 - We can see it is represented as JSON. When we are giving the " it is trying to neglect that using backslash

<img width="911" height="313" alt="image" src="https://github.com/user-attachments/assets/002f1a3a-92a7-4b4d-aa80-a39d3d7e37e0" />

- We trying many possibilities. 

<img width="945" height="324" alt="image" src="https://github.com/user-attachments/assets/3f49ec00-bb3c-4453-8d68-3c9a6a0b748c" />

- We can see the alert() escaped from the \ and also we can it to escape from the } also hence we using an arithmetic operations
  
<img width="961" height="262" alt="image" src="https://github.com/user-attachments/assets/7c9c3e52-d121-49c6-988e-03ab46977e33" />

<img width="923" height="246" alt="image" src="https://github.com/user-attachments/assets/e344354b-2da3-4578-bdf1-234f6507b5a9" />

- Hence by pasting this is search we can solve the lab. \"*alert(1)}//

<img width="1075" height="407" alt="image" src="https://github.com/user-attachments/assets/299c4e72-72fd-4c52-99e3-c8ed5e250dd2" />


# ------------------------------------------------------------------------------


# 13. Reflected XSS into HTML context with most tags and attributes blocked

<img width="792" height="311" alt="image" src="https://github.com/user-attachments/assets/925eb379-52f1-4e4b-b8a5-a4aff3a2490a" />

### Goal : To perform a cross-site scripting attack that bypasses the WAF and calls print().

### Ingredients : Exploit server, home, search, view post button.

<img width="868" height="527" alt="image" src="https://github.com/user-attachments/assets/d3729d88-9b9f-4f33-87a4-6dda139184e9" />


### Solving : 

- Since it is using the reflected xss first thing we have to do is searching an orbitary value in the serach box and see where are all it is used.

<img width="1095" height="562" alt="image" src="https://github.com/user-attachments/assets/e64b6598-0fbd-4ebd-b956-d20062dd85f9" />

- Since the search result is not used anywhere or no script is involved. Trying to inject normal xss. <img src=1 onerror="alert(1)"> We can these tags are blocked by WAF(Web application Firewall).

<img width="1179" height="357" alt="image" src="https://github.com/user-attachments/assets/67e0d4de-35be-4c25-b35e-4d7a7344dbc4" />

- Not all tags are restricted by the WAF(Web application Firewall). We can see <> tag is not restricted. We can find out which is tags are all not restricted by using intruder in burp. 

<img width="964" height="323" alt="image" src="https://github.com/user-attachments/assets/2275d1de-eecf-4c7b-828d-44c8a924b7d7" />

 <img width="1354" height="598" alt="image" src="https://github.com/user-attachments/assets/a8ddda41-f265-4fea-b6ad-8ab7a76921f6" />

- We can see the the body and xss tag is getting the 200 response. 

<img width="1062" height="416" alt="image" src="https://github.com/user-attachments/assets/37847a5d-79ee-4078-ae9d-2a9bf2ff9e59" />

- When we tried to use this body and paste the code. 

<img width="824" height="208" alt="image" src="https://github.com/user-attachments/assets/e9e6c158-5867-49c0-a430-798346f63489" />

- It says attribute not allowed. 

<img width="333" height="139" alt="image" src="https://github.com/user-attachments/assets/af61f9a8-1f7f-4de7-b817-98bcf82aa032" />

- Hence we are trying to find which attribute is allowed by WAF. 

<img width="657" height="365" alt="image" src="https://github.com/user-attachments/assets/329081ea-b925-483d-b154-581401a2cbda" />

- We found some attribute that would bypass the WAF. We will choose the onresize attribute. We can see on changing the page size it triggers the print however we want to do it automatically when page is loaded hence we use the exploit server. 

<img width="847" height="522" alt="image" src="https://github.com/user-attachments/assets/049668a9-8fb0-40bd-8aad-9c134f0c9236" />

- Hence by uploading the following we can able to solve the lab. 

<img width="1210" height="273" alt="image" src="https://github.com/user-attachments/assets/d343c22e-edb7-4725-8b30-2d4330a7990b" />

# -------------------------------------------------------------------------------

# 14. Stored DOM XSS 

<img width="756" height="87" alt="image" src="https://github.com/user-attachments/assets/cd9e5ee2-942d-4ade-af00-d7bf3715172b" />

### Goal :  To call alert(). 

### Ingredients : Home and view post button. 

<img width="1019" height="500" alt="image" src="https://github.com/user-attachments/assets/62508469-9449-4a06-95e9-1bcb39efb4df" />

### Solving : 

- We try to submit an html commment.  

<img width="812" height="596" alt="image" src="https://github.com/user-attachments/assets/d7d42086-2933-45c3-8469-2bddfd8e62c2" />

- It has the html tag escape functionality. But we can see it is encoded properly. it missed to encode the closing </h1>. 

<img width="774" height="561" alt="image" src="https://github.com/user-attachments/assets/cba64d3d-729e-4186-8160-5f8532cedd63" />

- Hence we try to exploit that.

<img width="792" height="578" alt="image" src="https://github.com/user-attachments/assets/3753f1d1-4fb7-49ed-a8a2-a0eb1155098c" />

- We can see it is worked. 

<img width="754" height="434" alt="image" src="https://github.com/user-attachments/assets/8079fa15-6774-4a0b-a90f-74b02e697950" />

- Now we post our alert malicious payload. 

<img width="859" height="587" alt="image" src="https://github.com/user-attachments/assets/d035416b-d9cc-46ee-8c2c-2a31a991245c" />

Hence by posting that we solve the lab. 


# -------------------------------------------------------------------------------

# 15. Reflected XSS into HTML context with all tags blocked except custom ones 

<img width="716" height="125" alt="image" src="https://github.com/user-attachments/assets/72a5d00a-a241-4525-ad87-43e72155e515" />

### Goal :   To perform XSS attack that injects a custom tag and automatically alerts document.cookie. 

### Ingredients : Home, exploit server, search and view post button. 

<img width="890" height="483" alt="image" src="https://github.com/user-attachments/assets/bcb549f7-72f2-4711-b4d3-098a29376e21" />

### Solving : 

As like previous apps mostly all tags '<>'  are blocked. 

- We can see not all the tags are blocked the custom tag is still not blocked. 

<img width="807" height="350" alt="image" src="https://github.com/user-attachments/assets/3b56268e-47fc-4619-90e7-f8067c3bc0af" />

- We create the payload properly like. <custom-tag onfocus='alert()' id='x' tabindex=1> </custom-tag>
- onfocus='alert()' --> It will trigger alert when onfocusing.
- tabindex=1 --> so it always comes first. 

<img width="1053" height="561" alt="image" src="https://github.com/user-attachments/assets/93775481-db80-4ee1-b88b-1fc148e5022e" />

- We can see all are injected in the properly. We want it to run for the attacker hence submitting in the server.

 <img width="818" height="176" alt="image" src="https://github.com/user-attachments/assets/7a3c6c1d-05e2-4b27-a59b-71eb9f3e1241" />

- Hence by posting this we can solve the lab.

# ------------------------------------------------------------------------------

# 16. Reflected XSS with some SVG markup allowed

<img width="722" height="106" alt="image" src="https://github.com/user-attachments/assets/ac6e0457-7cac-41b8-a2cc-a94607ca9668" />

### Goal :  To call an alert() by using the allowed svg mark up. 

### Ingredients : Search, Home and view post button. 

<img width="941" height="426" alt="image" src="https://github.com/user-attachments/assets/c8548916-150a-4e9b-a6b2-da1d553d08e3" />

### Solving : 

- As usual we will try to inject the alert() via img tag. Its says tags not allowed.

<img width="382" height="235" alt="image" src="https://github.com/user-attachments/assets/f9af976c-5da8-4e9f-854f-979d00a1d1a0" />

- Hence we are intercepting the request in the burp and see which tag can be used. We can see these tags are allowed.

<img width="877" height="176" alt="image" src="https://github.com/user-attachments/assets/7b7d700b-70fd-4ddb-b267-284ac932db68" />

- We have the tag which is allowed we try to find the attribute which is allowed using intruder. 

<img width="1254" height="422" alt="image" src="https://github.com/user-attachments/assets/d74cf748-4e73-4deb-b1dc-22e131b4bfd8" />

- We can it is only allow the onbegin. What onbegin would do is execute the code on begining the animation. 

<img width="640" height="274" alt="image" src="https://github.com/user-attachments/assets/ce702c97-1b1f-490a-b2ab-6a869da12b77" />

- Hence by doing the following we solve the lab. 

<img width="727" height="285" alt="image" src="https://github.com/user-attachments/assets/974b3a46-290b-4d1c-86e1-e9a71651ad04" />


# ------------------------------------------------------------------------------

# 17. Reflected XSS in canonical link tag

<img width="789" height="359" alt="image" src="https://github.com/user-attachments/assets/c4b290e2-fe8c-4258-91b0-02f1d5fbfbc6" />

### Goal :  To call alert() as they are using the canonical link tags. 

### Ingredients : Home, view post button. 

<img width="885" height="556" alt="image" src="https://github.com/user-attachments/assets/6d659a13-e980-4373-a345-27fce8ffe345" />

### Solving : 

- We can see the lab is reflected xss but can't see any reflecting element like search we can only see the url. We try to inject alert() there and when seeing the page source it is using the canonical tag. 

 <img width="1142" height="386" alt="image" src="https://github.com/user-attachments/assets/be989b9e-79d3-4ed8-9c2f-c6790cd934c6" />

- Even though have injected the code here we can't make click on this because it is reflected on the UI it is only in the url. Hence we are going to use the attribute called access key. It is used to create keyboard shortcuts for an element. So we can able submit, click or do some events by giving that.

<img width="1238" height="431" alt="image" src="https://github.com/user-attachments/assets/d5cb6f16-b959-43bb-80be-259394a06ed0" />

# ------------------------------------------------------------------------------


# 18.  Reflected XSS into a JavaScript string with single quote and backslash escaped

<img width="731" height="173" alt="image" src="https://github.com/user-attachments/assets/65c5ff4f-2dcc-4747-8576-221981d78416" />

### Goal : To perform xss that would break out of Javascript string and call alert().

### Ingredients : Home, view post button. 

<img width="887" height="536" alt="image" src="https://github.com/user-attachments/assets/0a4db7f0-0e32-4b67-a533-68eb0e6182f9" />

### Solving : 

- Since it is using the reflected xss first thing we have to do is searching an orbitary value in the serach box and see where are all it is used.

<img width="1055" height="534" alt="image" src="https://github.com/user-attachments/assets/7a94ac64-fbdb-437b-a350-90a5bd8e6235" />

- We can see it is collecting the value in the variabe called searchTerms. and when we try escape the string by using the ' it is escaping by using the /

<img width="1065" height="485" alt="image" src="https://github.com/user-attachments/assets/a38cd1ec-414f-415a-b8b6-6e4da47347a8" />

- Even though we string come out of the string using the \ it is also escaped using another \. Hence we should try to come out of the </script> itself.

<img width="1192" height="521" alt="image" src="https://github.com/user-attachments/assets/6309f6f6-3b3b-40e2-b859-d4fde26fafe2" />

- We can see it is worked. Why it is worked means usually it should consider the input as html but here it has the vulnerability which it consider this as script tag and close the tab and we can inject the payload in a new script tag. 

# ------------------------------------------------------------------------------


# 19. Reflected XSS into a JavaScript string with angle brackets and double quotes HTML-encoded and single quotes escaped

<img width="744" height="176" alt="image" src="https://github.com/user-attachments/assets/c30fed6a-17fa-4072-9ee4-f46584ed18c4" />

### Goal : To perform xss that would break out of Javascript string and call alert().

### Ingredients : Same as above. 

### Solving : 

- We try the all the possibilty including the last lab solution. But here it is completely url encoded. 

<img width="1084" height="563" alt="image" src="https://github.com/user-attachments/assets/68540566-024d-4454-9687-46e7d14e5e4a" />

- We can escape the backslash using another backslash and using the - operator because + is url encoded in JS. Still we can't break out of the string which is closed by'  

<img width="1150" height="603" alt="image" src="https://github.com/user-attachments/assets/defe96cf-eb37-415c-b854-e4700dcec5b6" />

- We can break out of the string by using the forward double slash \\. And we can see it taken '//' as string and alert pop up and neglect the ' Hence lab solved. 

<img width="1102" height="549" alt="image" src="https://github.com/user-attachments/assets/24c22968-8a35-48f7-b785-1696d49ae562" />


# ------------------------------------------------------------------------------


# 20. Stored XSS into onclick event with angle brackets and double quotes HTML-encoded and single quotes and backslash escaped

<img width="714" height="111" alt="image" src="https://github.com/user-attachments/assets/36d9a99d-9c51-4d22-9b3e-c0ffdf887de4" />

### Goal : Submit a comment that calls an alert() when author name is clicked. 

### Ingredients : Home, view post, comment section. 

### Solving : 

- Trying to submit a simple random comment and see the code flow

<img width="774" height="592" alt="image" src="https://github.com/user-attachments/assets/8ef49eef-f0cd-4c85-84ed-ebb3291609c2" />

- It is taking the website in a href in the author when clicking that it redirects to the page. Here may be the vulnerability we will try to exploit that. Inside the <a they have some javasrcipt to santize the input.   

<img width="787" height="458" alt="image" src="https://github.com/user-attachments/assets/463c5da0-7577-4e45-8ab5-f40d986a2a93" />

- Even though the angle brackets and double quotes HTML-encoded and single quote are backslash escaped. We will try to test that and we can see single quotes are back slash escaped. 

<img width="1037" height="518" alt="image" src="https://github.com/user-attachments/assets/724a080f-5972-418d-acc0-7ee738bd6c89" />

- We will try give the encoded value as the input and see what happens. We will try this http://foo?&apos;-alert(1)-&apos; . We can see it worked. 

<img width="1204" height="484" alt="image" src="https://github.com/user-attachments/assets/a45eeef2-7eee-4b2d-b929-426a0c13ca4f" />

- &apos --> url encoded value of ' and  We will what is happening in the code. It is html decoded from &apos to '.
- The server sanitize the input where it will be &apos; only so there html decoding happening so no backslash for escaping ' but when in the browser it is getting html decoded and changed to ' and no backslash is escaping.  

<img width="862" height="390" alt="image" src="https://github.com/user-attachments/assets/17a5058a-e2d5-44cd-a595-b3a4e841ef7a" />

- When we are viewing the pagesource we can see that it is sending the input to the browser as normal string as we given only but it in the broswer only as a process it is html decoded.

<img width="1246" height="202" alt="image" src="https://github.com/user-attachments/assets/17a5cad7-b1af-436c-bdb7-5c6e3c4b20dd" />
 
# ------------------------------------------------------------------------------


# 21. Reflected XSS into a template literal with angle brackets, single, double quotes, backslash and backticks Unicode-escaped

<img width="747" height="137" alt="image" src="https://github.com/user-attachments/assets/27d0e704-5a21-451a-8c86-3021c40cecc3" />

### Goal : To perfrom XSS that calls alert() inside the template. 

### Ingredients : Home, search and view post button. 

<img width="920" height="556" alt="image" src="https://github.com/user-attachments/assets/f2790367-a8bf-4684-8911-7dda29c49a4a" />

### Solving : 

- Since it is using the reflected xss first thing we have to do is searching an orbitary value in the serach box and see where are all it is used.

<img width="938" height="465" alt="image" src="https://github.com/user-attachments/assets/1cb4df49-42e7-469e-b9e5-ec5fae6c81e3" />

- We can see it is used inside the <script> and inside the (`) which is called template literal.
- Template literal is a template representation used to reduce the code length. If we are using a string and want to include a variable means its representation would be 'string' + myVar + 'string'. So we have break out of string every time we want to use a variable but in template literal we can just give like  ${myVar} inside a templete literal ` we can able to include the variable.
- Since it is using te template variable we will try to call the alert inside the `` like ${alert(1)}.

<img width="1075" height="461" alt="image" src="https://github.com/user-attachments/assets/742599a0-ca9a-46d5-838b-14bf5e829cf8" />

- Hence by doing this we solved the lab. 

# ------------------------------------------------------------------------------

# 22. Exploiting cross-site scripting to steal cookies

<img width="763" height="143" alt="image" src="https://github.com/user-attachments/assets/27772f97-84bb-4e3a-8887-c8d5244cb004" />

### Goal :  To perfrom XSS to steal cookie then use the cookie to impersonate the victim. 

### Ingredients : Home, Myaccount, view post button. 

<img width="930" height="507" alt="image" src="https://github.com/user-attachments/assets/4a319985-84a4-4993-b6b0-7a524565ee1f" />

### Solving : 

- Since the target server interacts with a url we will use burp collobarator to collect the request.

 <img width="794" height="599" alt="image" src="https://github.com/user-attachments/assets/dbd355ab-3f74-4879-bbc2-e0bb8a4062ef" />

- We can see the comment section is completely vulnerable no santisation is happening there. 

 <img width="730" height="381" alt="image" src="https://github.com/user-attachments/assets/809dd2a1-4124-4cf5-a861-f965638a34e4" />

- Hence we will try to make the victim send the cookie to our collobartor by submitting the following script.

<img width="791" height="574" alt="image" src="https://github.com/user-attachments/assets/6c3a1fc0-636a-47c5-9a32-0efa4f01c1cd" />

-  fetch --> Send request to this attaker server
method: 'POST', -> so cookie is send
mode: 'no-cors', -> it allow to read 
body:document.cookie --> getting the session cookie.

<img width="929" height="607" alt="image" src="https://github.com/user-attachments/assets/66b588f7-8330-4d5e-aa12-6a1ed4713175" />

- We try to inject the cookie in the request.

<img width="969" height="594" alt="image" src="https://github.com/user-attachments/assets/f82679ac-87a9-4825-a2e8-b4cc6a391c59" />

<img width="1132" height="619" alt="image" src="https://github.com/user-attachments/assets/70714e38-0a28-4bdc-825a-636951232ad1" />


# ------------------------------------------------------------------------------





 














