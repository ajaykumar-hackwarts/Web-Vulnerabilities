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


5. 








