Cross-Site Scripting(XSS) is a attack where attacker injects malicious javascript into a trusted website so when another users visit the page the browser runs the script as if like it comes from the script. 
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


5. DOM XSS in jQuery anchor href attribute sink using location.search source

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


6. DOM XSS in jQuery selector sink using a hashchange event

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


7. Reflected XSS into attribute with angle brackets HTML-encoded

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


8. 


























