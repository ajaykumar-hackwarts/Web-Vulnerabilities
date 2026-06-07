# **SQL Injection** : It is a vulnerability which allows attacker to interfere with the queries that application makes to the database. 

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

# 3. SQL injection attack, querying the database type and version on Oracle

<img width="772" height="98" alt="image" src="https://github.com/user-attachments/assets/9686c1b9-93bd-470a-9b62-5a5f6bd2e956" />

### **Goal** : To display database version string. 

### **Ingrediants** : Home & Category button. 

<img width="1239" height="500" alt="image" src="https://github.com/user-attachments/assets/c1383ac0-da30-4909-9475-58ac5f2268b6" />

### **Solving** : 

- Lets check it is vulnerable to SQLI or not by introducing ' in the query. And we can see it is vulnerable. 

<img width="1094" height="495" alt="image" src="https://github.com/user-attachments/assets/70471a9a-eec5-4041-8b36-5d14469e159a" />

- We will use burp suite to solve this lab. Firstly we will check how many columns it has by using order by 1 -- and increase the value till it says internal sever error. 

<img width="1024" height="485" alt="image" src="https://github.com/user-attachments/assets/bb652dc9-53b0-44c5-8179-0e7012ad136f" />

<img width="1043" height="508" alt="image" src="https://github.com/user-attachments/assets/654c125e-209f-42f0-ad35-a256ec255c74" />

<img width="1095" height="555" alt="image" src="https://github.com/user-attachments/assets/40f42d37-6dfd-4a15-9aa3-fa348ff6eec9" />

- Hence it has 2 columns. Now we will find data type of the 2 columns by using UNION SELECT 'a' , 'a' FROM dual. Extra FROM dual because it is using the oracle database.

<img width="1070" height="454" alt="image" src="https://github.com/user-attachments/assets/f1258aa8-25d9-4b10-b762-2b0ef58bf1cb" />

- Hence we found both the columns are string. Now the last step we will output the version of the oracle using the query from the cheat sheet. 

<img width="892" height="430" alt="image" src="https://github.com/user-attachments/assets/e81d7efe-bbf7-42af-80a9-70093bb0b739" />

- By pasting this we can solve the lab UNION SELECT banner, NULL FROM v$version

<img width="1235" height="556" alt="image" src="https://github.com/user-attachments/assets/e9877349-94a8-4563-add0-75a35750c787" />

<img width="1235" height="556" alt="image" src="https://github.com/user-attachments/assets/793ce434-342f-4c79-8bbd-4eff32bf6bcb" />


# ------------------------------------------------------------------------------


#4. SQL injection attack, querying the database type and version on MySQL and Microsoft

<img width="759" height="110" alt="image" src="https://github.com/user-attachments/assets/13c4107a-ad7d-48cc-8f10-3c9563fd115d" />

### **Goal** :   To display data version string. 

### **Ingrediants** : Home & Category button. 

<img width="1274" height="401" alt="image" src="https://github.com/user-attachments/assets/2110ab35-b1cc-4a55-9c25-1437ccd10fee" />

### **Solving** : 

- Lets check it is vulnerable to SQLI or not by introducing ' in the query as usual. And we can see it is vulnerable.

<img width="1067" height="487" alt="image" src="https://github.com/user-attachments/assets/192994d7-3f1a-4e67-9de7-877d23b518b6" />

- We will use burp suite to solve this lab. Firstly we will check how many columns it has by using order by 1 -- and increase the value till it says internal sever error. But we could see it shows an error 

<img width="1305" height="462" alt="image" src="https://github.com/user-attachments/assets/ef8e7b73-9f29-4e17-9f78-0d8cce017fa0" />

- Since it is not using the oralce database we will try this payload order by 1# and we can see it worked and it having 2 columns only

<img width="1162" height="420" alt="image" src="https://github.com/user-attachments/assets/15a6f384-a136-48af-b334-30d41832680c" />

<img width="1188" height="510" alt="image" src="https://github.com/user-attachments/assets/131e0f7a-f6ad-476d-a240-6dccd19a48b8" />

<img width="1347" height="604" alt="image" src="https://github.com/user-attachments/assets/4dd94de7-8d46-431b-a6c1-c27eb768cc4d" />

- Now we will find data type of the 2 columns by using UNION SELECT 'a' , 'a'#. Hence we can see it is in response  

<img width="1213" height="518" alt="image" src="https://github.com/user-attachments/assets/b8bc27de-cab4-4d18-b356-44f65b79b01e" />

- By pasting this we can solve the lab UNION SELECT @@version, NULL# we can display the version and solved the lab. 

<img width="713" height="353" alt="image" src="https://github.com/user-attachments/assets/94693422-33d3-4561-bc84-5c2393937c11" />

<img width="1308" height="484" alt="image" src="https://github.com/user-attachments/assets/8c27d3a6-3888-44fd-be35-62c08200dd39" />

<img width="1330" height="519" alt="image" src="https://github.com/user-attachments/assets/f31e8647-d152-42f6-9272-c69750114d61" />


# ------------------------------------------------------------------------------

# 5. SQL injection attack, listing the database contents on non-Oracle databases

<img width="772" height="270" alt="image" src="https://github.com/user-attachments/assets/855d6ae5-7f5f-4b15-9697-540c7afa99ad" />

### **Goal** :  To determine the table which contains username and password output the content of the table and finally login as the administrator user. 

### **Ingrediants** : Home, Category & My account button. 

<img width="1300" height="438" alt="image" src="https://github.com/user-attachments/assets/89d40c5f-84e3-4001-b7f3-4de83cfb4905" />

### **Solving** : 

- Lets check it is vulnerable to SQLI or not by introducing ' in the query as usual. And we can see it is vulnerable.

<img width="916" height="358" alt="image" src="https://github.com/user-attachments/assets/25fbc050-adcb-41ed-b1f1-b682ee54b960" />

- We will use burp suite to solve this lab. Firstly we will check how many columns it has by using order by 1 -- and increase the value till it says internal sever error.

<img width="1294" height="470" alt="image" src="https://github.com/user-attachments/assets/fd055313-a613-4ac4-ae16-1533d55c7586" />

<img width="1176" height="524" alt="image" src="https://github.com/user-attachments/assets/5bbbf5c0-5ad3-406b-8894-e1f7a65b1d5c" />

- Hence it has 2 columns. Now we will find data type of the 2 columns by using UNION SELECT 'a' , 'a'--. Hence we can see both the data type is string. 

<img width="1139" height="452" alt="image" src="https://github.com/user-attachments/assets/3e77e466-6670-48c4-a058-f13edaa89e54" />

-  Next we have to find the version of the database for that first we have to find the which type of data base it is using  

<img width="713" height="353" alt="image" src="https://github.com/user-attachments/assets/94693422-33d3-4561-bc84-5c2393937c11" />

<img width="1351" height="560" alt="image" src="https://github.com/user-attachments/assets/849d1be5-e18e-4983-a731-fe7fcdc8cb17" />

<img width="1217" height="530" alt="image" src="https://github.com/user-attachments/assets/959d763c-f7c1-4c7e-bea9-352ab36549fe" />

<img width="1284" height="437" alt="image" src="https://github.com/user-attachments/assets/aa9d730c-a018-4f5b-9230-a3fb07e3e8aa" />

- It is using Postgre SQL not microsoft. Next we will get the output the list of tables.

<img width="818" height="522" alt="image" src="https://github.com/user-attachments/assets/acda3e62-3c74-4ad4-a600-24eb227b59fb" />

- We will search information_schema.tables in browser to we found it has table_name

<img width="604" height="411" alt="image" src="https://github.com/user-attachments/assets/0b329af3-7057-4469-8ab9-e0d358e043b3" />

- Hence the comment would be UNION SELECT table_name, NULL FROM information_schema.tables--. NULL because it has 2 columns.  Hence we got the table name of the users. users_tlhtaj

<img width="1244" height="515" alt="image" src="https://github.com/user-attachments/assets/478ebba0-8d65-40d8-b2ac-b16aa003cfff" />

- Lets find the column names of the users_tlhtaj. UNION SELECT column_name, NULL FROM information_schema.columns WHERE table_name = 'users_tlhtaj' 

<img width="1332" height="568" alt="image" src="https://github.com/user-attachments/assets/2af8d8af-763f-40b0-ba9e-eca8c97ee469" />

-  We got the username column name and password column name username_wlxwdz, password_lallgr by pasting this UNION SELECT username_wlxwdz, password_lallgr FROM users_tlhtaj-- we can find the administrator user name and password. 

<img width="1298" height="563" alt="image" src="https://github.com/user-attachments/assets/6b8c14e0-a670-4f89-980a-d716482c4699" />

<img width="1141" height="533" alt="image" src="https://github.com/user-attachments/assets/cb6a12f6-e040-4000-9969-183c1cd54b5c" />

- Hence by using the username and password we have logged in as the administrator.

# ------------------------------------------------------------------------------


# 6. SQL injection attack, listing the database contents on Oracle

<img width="762" height="262" alt="image" src="https://github.com/user-attachments/assets/3a627429-1170-4742-a74d-4e14a1f7ac8a" />

### **Goal** :  To determine the table which contains username and password output the content of the table and finally login as the administrator user. 

### **Ingrediants** : Home, Category & My account button. 

<img width="1280" height="447" alt="image" src="https://github.com/user-attachments/assets/8e773254-face-4a5e-a8a8-4fc68ca992ec" />

### **Solving** : 

- Since it will vulnerable to SQLI skipping the part of checking with ' and find the number ciolums by ' order by 1--

<img width="1240" height="493" alt="image" src="https://github.com/user-attachments/assets/f460f83a-263b-4e62-8ed9-b86db0609b18" />

<img width="1329" height="535" alt="image" src="https://github.com/user-attachments/assets/985f6b9e-3f1e-4b46-a3e7-d7c8dccf417f" />

- Hence it has 2 columns. Now we will find data type of the 2 columns by using UNION SELECT 'a' , 'a' FROM dual. Extra FROM dual because it is using the oracle database.

<img width="1234" height="443" alt="image" src="https://github.com/user-attachments/assets/7629c0b3-2563-4f96-b2bd-c4de9ca20339" />

- Next we will get the output the list of tables. 

<img width="869" height="451" alt="image" src="https://github.com/user-attachments/assets/7fb3fd23-032a-4398-bdc7-056b26d9facb" />

<img width="1212" height="490" alt="image" src="https://github.com/user-attachments/assets/ee567e61-7e36-4cec-8e3a-5e0451c2f426" />

- Hence the comment would be UNION SELECT table_name, NULL FROM all_tables--. NULL because it has 2 columns.  Hence we got the table name of the users.  
  
<img width="1204" height="439" alt="image" src="https://github.com/user-attachments/assets/e389ae89-fe06-446a-97fd-09216beb4eba" />

- Lets find the column names of the USERS_WCMTXX. UNION SELECT column_name, NULL FROM all_tab_columns WHERE table_name = 'USERS_WCMTXX' 

<img width="1203" height="421" alt="image" src="https://github.com/user-attachments/assets/5cb19ad7-e103-4587-996a-5a069ea2246d" />

 - We got the username column name and password column name USERNAME_KUYFPM, PASSWORD_YGRYCP by pasting this UNION SELECT USERNAME_KUYFPM, PASSWORD_YGRYCP FROM USERS_WCMTXX-- we can find the administrator user name and password. 

<img width="1352" height="537" alt="image" src="https://github.com/user-attachments/assets/a0a46088-5e55-41bd-8d09-6d936e52a0f4" />

<img width="1241" height="541" alt="image" src="https://github.com/user-attachments/assets/893d1a9c-f214-49bb-acae-e3dccd1da079" />

- Hence by pasting this we can solve the lab.





