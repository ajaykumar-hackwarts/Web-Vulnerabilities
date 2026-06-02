**SQL Injection** : It is a vulnerability which allows attacker to interfere with the queries that application makes to the database. 

# 1. SQL injection vulnerability in WHERE clause allowing retrieval of hidden data

<img width="774" height="192" alt="image" src="https://github.com/user-attachments/assets/4c9b68b0-c03f-45d0-b620-3a5a3dd27000" />

### **Goal** : To perform SQLI attack that reveal one or more unreleased product.

### **Ingrediants** : Home, View details, all etc buttons are there. 

<img width="1241" height="451" alt="image" src="https://github.com/user-attachments/assets/d77ac126-b2b6-497f-a848-c99735fe9353" />

### **Solving** :
 
- As given the problem statement When the user selects a category it will carry the SQL query as the following.

- SELECT * FROM products WHERE category = 'Gifts' AND released = 1

- When we select the categrory it returned the url like the following 

<img width="1236" height="667" alt="image" src="https://github.com/user-attachments/assets/046465bb-41f1-43c2-b8f8-04e9e3dac3e5" />

- First we will try the payload ' to check it is vulnerable to SQLI or not and it shows internal server error hence it is vulnerable. 

<img width="996" height="403" alt="image" src="https://github.com/user-attachments/assets/71fc3c83-53c5-4d4d-af01-717513c9eaea" />

- Then when we tried '-- this it will neglect all the query after this "--" 

<img width="1068" height="631" alt="image" src="https://github.com/user-attachments/assets/45384251-d24d-4f0c-9b69-2cc9097e39d8" />

- Then we add ' or 1=1--  because SELECT * FROM products WHERE category =   this is the query structure it will display all the products from the category and since 1=1 is always true. Hence by pasting this we solve the lab. 

<img width="1113" height="570" alt="image" src="https://github.com/user-attachments/assets/3e1ca864-63f8-48d1-b6e6-b4f925f9021b" />


# ------------------------------------------------------------------------------


# 2.  SQL injection vulnerability allowing login bypass

<img width="749" height="115" alt="image" src="https://github.com/user-attachments/assets/1cb77178-0be9-4bde-9f0a-ab85493a240c" />

### **Goal** : To perform SQLI that logs in to the application as the administrator user. 

### **Ingrediants** : Home, My account and view details button. 

<img width="1291" height="583" alt="image" src="https://github.com/user-attachments/assets/591ef804-5472-4194-beec-87c4b5a640ba" />

### **Solving** : 

 - First we will try to login with admin and see what hapens. We can notice that it is giving an non-verbose(Less Verbal) replay like invalid username or password. Which is good because if it where like invalid username alone or invalid password the attacker can enumerate username or password.     
   
<img width="1252" height="527" alt="image" src="https://github.com/user-attachments/assets/2f4995a0-a53f-4ddf-94de-7264bdc02cbe" />

- When we tried to break the query by inputting the ' in the input field we can see it is showing the internal server error it means it is vulnerable to SQLI

<img width="654" height="430" alt="image" src="https://github.com/user-attachments/assets/8b2b36cc-93f4-4da6-8e1d-94da4d926413" />

- Example : The code will be like SELECT FisrtName FROM users where username='' and password='' like this when we giving ' in the input it will be like username=''' so internal error occurs.

- Let's try to give username as administator and neglect the rest by giving like administator'--
- SELECT FisrtName FROM users where username='administator'--' and password=''
- Hence after -- everything is neglected. 

<img width="1014" height="593" alt="image" src="https://github.com/user-attachments/assets/56f3c023-3bd0-4c7f-ba00-591723f43e48" />

<img width="1047" height="528" alt="image" src="https://github.com/user-attachments/assets/1a9ebd40-a7d1-49c7-befd-a98a090ca7fc" />

# ------------------------------------------------------------------------------


