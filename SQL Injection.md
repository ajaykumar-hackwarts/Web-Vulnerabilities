<img width="1355" height="496" alt="image" src="https://github.com/user-attachments/assets/58b07d77-1ef4-491e-ad8a-b19c15907219" /># **SQL Injection** : It is a vulnerability which allows attacker to interfere with the queries that application makes to the database. 

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

# ------------------------------------------------------------------------------


# 7. SQL injection UNION attack, determining the number of columns returned by the query. 

<img width="758" height="230" alt="image" src="https://github.com/user-attachments/assets/48b4fe25-785b-4267-a9fd-56e48be0500d" />

### **Goal** : To determine to number of column returned by the query by UNION SQLI which will return addition null values. 

### **Ingrediants** : Home, Category, View details & My account button. 

<img width="1225" height="391" alt="image" src="https://github.com/user-attachments/assets/67af8970-7935-4860-969e-20deede9bbcf" />

### **Solving** : 

-  We will use burp suite to solve this lab. Firstly we will check how many columns it has by using order by 1 -- and increase the value till it says internal sever error.

 <img width="1212" height="529" alt="image" src="https://github.com/user-attachments/assets/7d9b7f77-288e-4efa-9e43-2d085415bff4" />

 <img width="1253" height="571" alt="image" src="https://github.com/user-attachments/assets/e342a08f-4a85-4a13-ab6f-ae36643a96f4" />

 <img width="1213" height="574" alt="image" src="https://github.com/user-attachments/assets/98de4e65-9510-4e07-bd92-c0b82e89aedb" />

 <img width="1326" height="551" alt="image" src="https://github.com/user-attachments/assets/1810d679-c645-4bdf-b2a0-d3e7368581e0" />

 - Hence the number of columns is 3.

<img width="1309" height="446" alt="image" src="https://github.com/user-attachments/assets/5c175c6b-22f3-4682-a4db-5ade6058ee5e" />

# ------------------------------------------------------------------------------

# 8.  SQL injection UNION attack, finding a column containing text

<img width="771" height="320" alt="image" src="https://github.com/user-attachments/assets/03584299-9750-4ad4-bea3-0200b4144fb3" />

### **Goal** : To perform UNION attack returns an additional row contains the value given in the lab.  Hence we can find which columns has the string data. 

### **Ingrediants** : Home, Category, View details & My account button.

<img width="1228" height="565" alt="image" src="https://github.com/user-attachments/assets/90eecec5-5be9-49b3-9f02-14ef9f24fb5f" />

### **Solving** : 

-  We will use burp suite to solve this lab. Firstly we will check how many columns it has by using order by 1 -- and increase the value till it says internal sever error.

<img width="1196" height="449" alt="image" src="https://github.com/user-attachments/assets/e2b1e02a-ef0a-4032-8a09-2c75c71b92a7" />

<img width="1209" height="506" alt="image" src="https://github.com/user-attachments/assets/11803b35-4040-486b-8338-34b81c7fb0cc" />

- It has 3 columns. Now we will find which column has the data type string by using UNION SELECT 'a', NULL, NULL-- iteratively like NULL, 'a', NULL-- and see which displays the additional column.

<img width="1180" height="392" alt="image" src="https://github.com/user-attachments/assets/909e4bea-e0ec-4941-855a-96522ed10970" />

<img width="1280" height="470" alt="image" src="https://github.com/user-attachments/assets/0c529df3-4ed4-4abe-8a8e-b7f056b034d9" />

<img width="1247" height="414" alt="image" src="https://github.com/user-attachments/assets/06f8bbd1-1e35-433d-b24b-3cde42f56cb7" />

<img width="1198" height="401" alt="image" src="https://github.com/user-attachments/assets/f07f5e8a-e799-4ea7-ad25-8e7b18c83059" />

- Hence the second column is of type string. Therefore by pasting UNION SELECT NULL, 'n5bleC', NULL-- we can solve the lab. 

<img width="1203" height="414" alt="image" src="https://github.com/user-attachments/assets/b74ad90b-0793-42e6-a081-64353ab58ad5" />

<img width="1328" height="491" alt="image" src="https://github.com/user-attachments/assets/fcf512c9-8dc9-4f4f-9727-d16e6fa0b8d3" />


# ------------------------------------------------------------------------------


# 9. SQL injection UNION attack, retrieving data from other tables

<img width="741" height="279" alt="image" src="https://github.com/user-attachments/assets/a5cc9be5-0c63-4c5c-96c9-ec5c6abfa337" />

### **Goal** : To perfrom UNION SQLI that will retrive all the usernames and password and using that we login as the administrator user. 

### **Ingrediants** : Same as above. 

### **Solving** : 

- We will use burp suite to solve this lab. Firstly we will check how many columns it has by using order by 1 -- and increase the value till it says internal sever error.

<img width="1205" height="464" alt="image" src="https://github.com/user-attachments/assets/4a88fd02-4760-416c-8ab1-d50af31bd336" />

<img width="1260" height="503" alt="image" src="https://github.com/user-attachments/assets/e9cb8e20-3503-4f6f-972c-b2b911768a2e" />

- Hence it has 2 columns. Now we will find data type of the 2 columns by using UNION SELECT 'a' , 'a'--. 

<img width="1225" height="399" alt="image" src="https://github.com/user-attachments/assets/93165928-d615-4e0d-9843-f5c106669bd8" />

-  Both column is of type string. Hence we can retrive data from another table using UNION because to diplay the username and password we have a condition that the two tables should have the same data type and number of columns. Therefore by pasting this we can retrive the username and password. UNION SELECT  username and password from users--

<img width="1308" height="458" alt="image" src="https://github.com/user-attachments/assets/420069f1-cffc-4d5c-bba7-7d53660fd476" />

- Hence we have the username and password of administrator user by using this we can solve the lab.

<img width="1217" height="518" alt="image" src="https://github.com/user-attachments/assets/c0f78330-22ae-4179-99b1-763701c218e1" />

# ------------------------------------------------------------------------------

# 10. SQL injection UNION attack, retrieving multiple values in a single column

<img width="760" height="255" alt="image" src="https://github.com/user-attachments/assets/fdcdfcf7-b5e0-4bff-9cf5-08628b06f5e7" />

### **Goal** : To retrive all the username and the password and log in as administrator. 

### **Ingrediants** : Same as above. 

### **Solving** : 

- We will use burp suite to solve this lab. Firstly we will check how many columns it has by using order by 1 -- and increase the value till it says internal sever error.

<img width="1176" height="478" alt="image" src="https://github.com/user-attachments/assets/58b7d895-7153-4efe-8710-5c733a5c3b4e" />

<img width="1285" height="509" alt="image" src="https://github.com/user-attachments/assets/19000814-7213-403a-977c-896adc41c11d" />

- Hence it has 2 columns. Now we will find from the 2 columns which has the data type string by using UNION SELECT 'a' , NULL-- and iteratively.

<img width="1196" height="433" alt="image" src="https://github.com/user-attachments/assets/1cb8869c-9f80-4fc9-8b62-3d805e5318dc" />

<img width="1230" height="418" alt="image" src="https://github.com/user-attachments/assets/b89cb6a4-310f-42b1-a987-f7797dd449a8" />

<img width="1246" height="464" alt="image" src="https://github.com/user-attachments/assets/feb8d069-f1d3-49fc-8fc7-636d74f21f16" />

- Since only one column is of type string we can't retrive the username and password in single comment. Hence we will use the cheat sheet.

<img width="755" height="456" alt="image" src="https://github.com/user-attachments/assets/8a4a226f-2752-49e3-b985-1ee46fcdfddc" />

- To do these we have to find which type of database it is using.

<img width="683" height="368" alt="image" src="https://github.com/user-attachments/assets/f4151937-f209-49f0-be06-dac86b090a2d" />

 <img width="1320" height="537" alt="image" src="https://github.com/user-attachments/assets/3474cf61-fd53-4d69-8158-97a4aba9473e" />

<img width="1365" height="502" alt="image" src="https://github.com/user-attachments/assets/06c8a3fc-ab0f-481b-8718-22251707cb66" />

- Hence it is using the postgre SQL. Therefore by pasting UNION SELECT NULL, username||password from users-- we can retrive the data. 

<img width="1360" height="568" alt="image" src="https://github.com/user-attachments/assets/63a26e13-dff4-4bc3-a073-72867a497a17" />

- Beautifying. 

<img width="1290" height="460" alt="image" src="https://github.com/user-attachments/assets/542802d4-8dce-4e6c-a0d5-74f44a52834a" />

<img width="1350" height="497" alt="image" src="https://github.com/user-attachments/assets/a5e96459-bb90-4a24-b83e-7debe098d1f0" />

# ------------------------------------------------------------------------------


11. Blind SQL injection with conditional responses.

<img width="761" height="314" alt="image" src="https://github.com/user-attachments/assets/db02ee82-6e51-4ef8-bd27-a432cb5a78bd" />

### **Goal** : To login as the administrator user as lab has Blind SQLI. 

Blind SQLI : Where database doesn't show the error directly instead they will show like delayed or change in response. 

### **Ingrediants** : Same as above. 

### **Solving** : 

- First we will find that the parameter is vulnerable to Blind SQLI by using the burp suite. If the tracking Id is correct it will return a welcome back message. 

<img width="1157" height="460" alt="image" src="https://github.com/user-attachments/assets/1e60cdd1-001a-4236-8951-da992c368f5a" />

- We will add some character to check that if the tracking is exist or not and welcome back message is coming or not. Hence If tracking id doesn't exist it will not give the welcome back message. 

<img width="1342" height="514" alt="image" src="https://github.com/user-attachments/assets/dbcd79e8-2a84-40ad-ba74-f87381931b46" />

- Now we will inject and test if it is vulnerable to Blind SQLI or not. By adding with ' and 1=1-- after the tracking id. 

<img width="1206" height="444" alt="image" src="https://github.com/user-attachments/assets/2816fe29-a674-489e-82b8-c78179300f74" />

<img width="1325" height="485" alt="image" src="https://github.com/user-attachments/assets/5ba6b928-cd56-4cbe-a899-01ca89389b05" />

- Hence it is reacting based on condition we can confirm it is vurnerable to Blind SQLI since it. By this we verify the users table exist or not like ' and (select 'x' from users LIMIT 1)='x'--

- If users table exist it will take x(orbitory value) from the table since we limit it by only one value is retrive at a time and x=x will come and give welcome back message indicate the users table exist.

<img width="1177" height="450" alt="image" src="https://github.com/user-attachments/assets/7d818bf8-12d2-4336-a787-d3b902994c44" />

- Hence we can see users table exist. Next we will confim that the username administrator exist in the users table or not by pasting ' and (select username from users where username='administrator')='administrator'--

<img width="1252" height="500" alt="image" src="https://github.com/user-attachments/assets/4dec6fd0-5b6a-4649-952a-7dffe6bbad76" />

- Username administrator does exist. By the same way we can check the password one by one like ' and (select password from users where username='administrator')='welcome121'-- like on by one. 

- But it is not a good way of doing that because we can do that it in the login page in the UI by brute force we don't need this srcipt or burp suite. 

- Hence we will try each charater of the password where for the administrator user. for that first we have find the length of the password. By this script ' and (select username from users where username='administrator' and Length(password)>1)='administrator'--

- And we will iterate the value 1 to 2 then 3, 4 and so on until it will not show welcome back message by using the burp suite intruder.

<img width="1179" height="477" alt="image" src="https://github.com/user-attachments/assets/93978b02-b5df-4cf2-ab4c-47b05c0e3e46" />

- We can see till 19 we get the welcome back message and length is same from 20 it changes and no welcome back message. Hence the password length is 20. 

<img width="1175" height="425" alt="image" src="https://github.com/user-attachments/assets/f2bc621f-649b-4bd0-a3ba-5b1e69f6b4f7" />

- Now we will find the first character of the password by brute forcing the alphanumeric values like ' and (select substring(password, 1, 1) from users where username='administrator')='a'--

<img width="1087" height="540" alt="image" src="https://github.com/user-attachments/assets/9ae269a7-fed2-48ae-9827-de9945988608" />

- We have founder the first character of the password by this we have to find all the character of the password. For this we have to iterate two values one is substring(password, 2, 1) and another is  ='a'--. Hence we will use the attacker type called cluster bomb and give two payload.

<img width="1318" height="560" alt="image" src="https://github.com/user-attachments/assets/4dfca8c0-8621-4580-884d-c1dda51a9cee" />

- These are 20 characters of the password. By arranging them sequentially we can login as administrator. 

<img width="1015" height="497" alt="image" src="https://github.com/user-attachments/assets/8292e1ca-94ff-447d-8e9a-f33bd2db8fbf" />

- The password is 392rl7bk9gtq4qbh1uq2. Hence we can login as the administrator user and solve the lab.

<img width="1197" height="509" alt="image" src="https://github.com/user-attachments/assets/dbab2724-2574-4a4e-a372-9b22183b23d1" />
 
# ------------------------------------------------------------------------------

# 12. Visible error-based SQL injection

<img width="733" height="197" alt="image" src="https://github.com/user-attachments/assets/36ebc346-818b-4e11-974c-6dd6c04e6247" />

### **Goal** : To leak the password from the error
 
### **Ingrediants** : Same as above. 

### **Solving** : 

- Since it is error based SQLI we will check the error by adding ' and we can see it is verbose error instead failing safe it is give us more detials hence we can exploit that. We can neglect the error by adding -- at the end. 

<img width="1341" height="472" alt="image" src="https://github.com/user-attachments/assets/cc98c2f3-790f-4b3a-a6a4-c8077306ea4a" />

- Lets use cast to display an error cast : change from one data type to another. Like ' and cast((select 1) as int)--. It throws an error that it should be type boolean

<img width="1318" height="423" alt="image" src="https://github.com/user-attachments/assets/c6c49d00-f44c-4ce8-b8a8-9c7b3ffcf424" />

- Hence we change and upload payload like ' and 1=cast((select 1) as int)--. Hence now it doesn't show that error. 

<img width="1200" height="421" alt="image" src="https://github.com/user-attachments/assets/43c029fa-62d9-419a-8ca5-a53e7a7da549" />

- We will use this script and modify it ' and 1=cast((select username from users) as int)-- like and to print the username

<img width="1351" height="418" alt="image" src="https://github.com/user-attachments/assets/2470ea82-c148-4fe8-a76d-686ff1c5ca53" />

- It shows an error as " Unterminated string literal started at position 95 in SQL SELECT * FROM tracking WHERE id = 'h3l4eM8Vy0KU3rVY' and 1=cast((select username from users) as' " as it exceeds the character as it completely ingores the last part " int)--"

- Hence we can neglect the tracking id so that we have the room for our script. Now it shows different error as 1 is not equal to string lists  like that. 

<img width="1353" height="471" alt="image" src="https://github.com/user-attachments/assets/76fa1bc5-c362-4b71-8da8-58591e9cf9c5" />

- We can solve this limit to one string like ' and 1=cast((select username from users limit 1) as int)-- and we can see it is displays the username administrator in the error 

<img width="1323" height="453" alt="image" src="https://github.com/user-attachments/assets/45d7b86c-118b-4578-94d7-f77958f26be7" />

- By the same way we can able to get the password. Like ' and 1=cast((select password from users limit 1) as int)-- and it revealed the password. 

<img width="1360" height="495" alt="image" src="https://github.com/user-attachments/assets/d9c9c6e9-3e1e-4117-bfa9-44d9fd0af843" />

- The password is vka1lc7yc4q652m0pe5b and we can use this login as administartor and solve the lab.

<img width="1256" height="499" alt="image" src="https://github.com/user-attachments/assets/d8570d35-4fdd-49cd-9290-d8ab4a0f6687" />

# ------------------------------------------------------------------------------

# 13. Blind SQL injection with time delays

<img width="746" height="241" alt="image" src="https://github.com/user-attachments/assets/8f42a1f6-d6b7-46eb-b6c5-568b4496c4e6" />

### **Goal** : To exploit SQLI that cause 10 second time delay. 

### **Ingrediants** : Same as above. 

<img width="1263" height="386" alt="image" src="https://github.com/user-attachments/assets/1043c243-5b3b-4df0-9f02-071b7486294c" />

### **Solving** :  

- Here tracking id is the vulnerable parameter. We will use burp exploit this and we will use the cheat sheet to find which data base it is using.  

<img width="734" height="297" alt="image" src="https://github.com/user-attachments/assets/ea8bf3e2-d114-4b6e-8e0d-8ceee002b6ac" />

- We will check one by one by concatinating with the tracking id.

<img width="1336" height="528" alt="image" src="https://github.com/user-attachments/assets/56456ba3-89a8-4352-bae0-fb5c0b2aca36" />

<img width="1365" height="520" alt="image" src="https://github.com/user-attachments/assets/81497ec5-5098-498a-84c0-39c5cb34a782" />

- Hence by with and without script the time taken is same hence it is not using MqSQL database. Let's try the next one.

 <img width="1350" height="589" alt="image" src="https://github.com/user-attachments/assets/edacbec0-5e57-416f-a855-1ce0c9aff762" />

 




