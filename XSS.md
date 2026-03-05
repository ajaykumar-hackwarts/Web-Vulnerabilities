Cross-Site Scripting(XSS) is a attack where attacker injects malicious javascript into a trusted website so when another users visit the page the browser runs the script as if like it comes from the script. 
Cross ---> Code from outside source
Site ---> runs inside a trusted site
Scripting --> attackers code runs on the victims browser. 


# 1. Reflected XSS into HTML context with nothing encoded 

### Goal : To perform cross-site scripting attack and call alert function. 

### Ingrediants : 

<img width="859" height="599" alt="image" src="https://github.com/user-attachments/assets/41778bbf-a7c7-45b0-9db2-5d71b57c4430" />

<img width="817" height="307" alt="image" src="https://github.com/user-attachments/assets/9932878a-1397-4ccf-a645-bfdde8d4a0ec" />

- Search, Home, view post button are there.

### Solving : 

Since the lab is vulnerabe for refelcted xss it means when we send a malicious script in the request the server immediately back to the page. And it says HTML context with nothing encoded we can simple write script like <script>alert(2)</script> 
and we can solve the lab. 

<img width="1254" height="471" alt="image" src="https://github.com/user-attachments/assets/9544e5bd-2f04-46d6-a307-1a0b966bdd9a" />


# -----------------------------------------------------------------








