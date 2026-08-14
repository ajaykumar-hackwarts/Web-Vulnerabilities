# Business Logic Vulnerabilities : It is a vulnerability where application works correctly as programmed but the business rules are flawed like the user manipulate and use the application as they shouldn't be able to.

## Example : Like app has a product for price 1000 and discount coupon is 10% and app accidentaly allows to apply the coupon for multiple times 

# 1. Excessive trust in client-side controls.

<img width="741" height="169" alt="image" src="https://github.com/user-attachments/assets/015d646d-a305-4750-86db-c82aa51eccb8" />

# Goal : To Buy a "Lightweight l33t leather jacket".

# Ingrediants : Home, My account, view details. 

<img width="1293" height="541" alt="image" src="https://github.com/user-attachments/assets/1e4755fc-2bd5-430e-8446-99452c643bae" />

# Solving : 

- Let's login and add the jacket to the cart.

<img width="915" height="554" alt="image" src="https://github.com/user-attachments/assets/d88f0040-69b7-4a9d-a1cb-56e7db52b875" />

<img width="1049" height="540" alt="image" src="https://github.com/user-attachments/assets/c9840e77-4897-43db-911d-c9bae72d7066" />

 <img width="1063" height="478" alt="image" src="https://github.com/user-attachments/assets/245a6db2-ffdb-42d9-91e9-956c6a13cac5" />

 - We can see that in the request it is sending the price in the request too. And when we sending the request using the repeater it is adding the item again 

<img width="877" height="561" alt="image" src="https://github.com/user-attachments/assets/4abe666c-04cb-458d-8a39-5f81873d8488" />

- Hence let's try that can we able to change the amount or not. We can able to change the price of the jacket

<img width="1011" height="500" alt="image" src="https://github.com/user-attachments/assets/50902097-dd7d-41de-a897-31582ff9381e" />

<img width="1037" height="599" alt="image" src="https://github.com/user-attachments/assets/7e757431-49ce-49fa-8425-bfaaa67b9d4e" />

- Hence by placing the order we solve the lab.

<img width="1036" height="470" alt="image" src="https://github.com/user-attachments/assets/43747825-e3b0-4767-8702-30d89f17c0f8" />


# ------------------------------------------------------------------------------

# 2. High-level logic vulnerability.

<img width="726" height="151" alt="image" src="https://github.com/user-attachments/assets/5d678d9b-7980-4788-83e2-cf0462d1f5b4" />

# Goal : Same as above

# Ingrediants : Same as above

# Solving : 

- Let's login and add the jacket to the cart. We can notice that we don't have price in the request as like the preivious lab.

<img width="1075" height="455" alt="image" src="https://github.com/user-attachments/assets/7e021f49-9188-4f3f-9088-32f1cdd05ce7" />

- We will try to send a negative value in the quantity and see the response in the UI and it is accepts the negative value.

<img width="1071" height="564" alt="image" src="https://github.com/user-attachments/assets/b7f9064a-5c8d-4b3e-8e97-5c4aa478bd09" />

- We will try to add some other and item and have negative value to that.

<img width="871" height="439" alt="image" src="https://github.com/user-attachments/assets/5b377220-ede4-4516-bc1d-336f465fe7bf" />

- Hence the negative value of the newly added item is subtracted from the leather jacket.

<img width="924" height="591" alt="image" src="https://github.com/user-attachments/assets/329d412a-5392-40d8-b5ca-7ed501c49e10" />

- Now we will place the order and solve the lab.

<img width="1120" height="461" alt="image" src="https://github.com/user-attachments/assets/135ef05a-c8c4-4525-9a79-ecf59bffdcec" />

# ------------------------------------------------------------------------------

# 3. Inconsistent security controls.

<img width="871" height="130" alt="image" src="https://github.com/user-attachments/assets/952af00f-0e67-4f0d-84d0-2ce113823b3c" />

# Goal : To access the admin panel and delete carlos user. 

# Ingrediants : Same as above

# Solving : 

-   We will try to fuzz the admin in the url. We can notice admin panel is there but for that we have to logged in as DontWannaCry user.

 <img width="1170" height="426" alt="image" src="https://github.com/user-attachments/assets/88f8dc32-1bad-4f71-a547-f8cbf59f7168" />
 
- We will use the exploit email first for getting the complete registration link.

<img width="1244" height="547" alt="image" src="https://github.com/user-attachments/assets/ee12bc0c-3300-49e0-9c62-acdbcac018ab" />

<img width="1321" height="590" alt="image" src="https://github.com/user-attachments/assets/099b8b95-d959-41da-8089-db109e7589cc" />

- Now we will update the email to access the admin panel.

<img width="1323" height="561" alt="image" src="https://github.com/user-attachments/assets/23e913ad-53a3-410e-b8b6-14405807c7ae" />

- Hence by deleting the admin panel we solved the lab.

<img width="1319" height="543" alt="image" src="https://github.com/user-attachments/assets/6e41a5b9-4293-4da2-a80c-1dffa3da5f76" />

# ------------------------------------------------------------------------------

# 4. Flawed enforcement of business rules.

<img width="804" height="145" alt="image" src="https://github.com/user-attachments/assets/313b209b-dfb2-47de-8c81-4985fded631d" />

# Goal : To buy a "Lightweight l33t leather jacket". 

# Ingrediants : Same as above

# Solving : 

- Let's login and add the leather to the cart and see the response.

<img width="1037" height="566" alt="image" src="https://github.com/user-attachments/assets/fff1068d-3fd9-4d42-8e83-af91fc67f54a" />

<img width="1260" height="506" alt="image" src="https://github.com/user-attachments/assets/7b661941-9b9b-4461-ad24-5b3b358ceeaa" />

- Lets check for some other features in the home page. There is a signup box and when we signup we got a coupon for that

<img width="1275" height="591" alt="image" src="https://github.com/user-attachments/assets/0fac923a-1ddf-4b62-8501-daf304a92c58" />

<img width="912" height="432" alt="image" src="https://github.com/user-attachments/assets/83d6bd72-fcba-4055-80d4-1b804d00448e" />

<img width="914" height="597" alt="image" src="https://github.com/user-attachments/assets/8c0c6261-cdd7-4f8f-a87e-6e6a2c0bc03b" />

- And we can see we can't contiously apply these coupons hence we will try alternatively apply the coupon.

<img width="1059" height="476" alt="image" src="https://github.com/user-attachments/assets/e95ca97f-fe6a-40c3-9759-796e1859285c" />

- After doing all this and placing the order we solved the lab.

<img width="1173" height="600" alt="image" src="https://github.com/user-attachments/assets/8ccea1f0-2b34-47e0-81bb-c18d97382ae5" />

# ------------------------------------------------------------------------------

# 5. Low-level logic flaw.

<img width="724" height="136" alt="image" src="https://github.com/user-attachments/assets/51a1e88f-66a6-4f9c-8faa-47faba3eec35" />

# Goal : Same as above

# Ingrediants : Same as above

# Solving : 

- Let's login and add the leather to the cart and see the response.

<img width="921" height="598" alt="image" src="https://github.com/user-attachments/assets/f31b1754-c49d-4e0d-b50c-ac7bb3230a6c" />

<img width="1166" height="496" alt="image" src="https://github.com/user-attachments/assets/23d727b6-f76a-4ed6-a14f-2077f0f66e1e" />

- We can see we can't able to add the negative value and no coupon is there hence we will try to add the heighest quantity and see if the application breaks and reacts differently.

<img width="1071" height="500" alt="image" src="https://github.com/user-attachments/assets/7318123a-1a65-4ecf-aec4-a9db72b361c8" />

<img width="1035" height="612" alt="image" src="https://github.com/user-attachments/assets/4e0c2d6d-af1c-4c59-8eff-63a9c8d6b8f8" />

<img width="1340" height="606" alt="image" src="https://github.com/user-attachments/assets/2561c2c4-448c-4de3-bc0e-36ffa2626a68" />

<img width="1165" height="587" alt="image" src="https://github.com/user-attachments/assets/d0ecdc1d-477a-4aa3-8249-ac7ca2c9a476" />

- It's keeps on increasing let's stop some where when it reacts differently.

<img width="1029" height="606" alt="image" src="https://github.com/user-attachments/assets/d406df43-947d-4ae1-9325-9bfe20660835" />

- We can see it reacts differently as giving the negative value at the 180 count of request. Hence when we increase the quantity of jacket the nagative price will be reduce.

<img width="1008" height="570" alt="image" src="https://github.com/user-attachments/assets/c0756fd3-5cef-410a-b5ce-daa25ce955c1" />

<img width="1244" height="612" alt="image" src="https://github.com/user-attachments/assets/a8f0041f-e188-46af-a3ae-a5832e9dd18c" />

- We calulating the number of request we want to send in order to buy the jacket by getting the price low by first we divide the price in there with the price of one jacket.  

<img width="952" height="473" alt="image" src="https://github.com/user-attachments/assets/0e5a2ab5-fd3c-4d66-ab06-6f231b0584b9" />

- Since we are sending 99 request at a time. Hence by following calculation we want to send 130 request to become the positive low price. 

<img width="874" height="502" alt="image" src="https://github.com/user-attachments/assets/8c697db0-6527-4e5c-881c-e8567dde7498" />

- Now we will another item to match teh price below positive 100.

<img width="902" height="575" alt="image" src="https://github.com/user-attachments/assets/b8eea425-95d1-4bbf-aa9c-9f0ba462b852" />

- Hence we matched the value. Thus by placing the order we solve the lab.

<img width="956" height="596" alt="image" src="https://github.com/user-attachments/assets/7e97401f-8f78-481e-b6f8-fd9f0dd51a76" />

<img width="1122" height="482" alt="image" src="https://github.com/user-attachments/assets/62770733-2077-475c-bfa5-ec5edc5f51b6" />

# ------------------------------------------------------------------------------


# 6. Inconsistent handling of exceptional input.

<img width="761" height="107" alt="image" src="https://github.com/user-attachments/assets/6f2f0af5-1bf8-44ab-8e83-bdd6728d7968" />

# Goal : Access the admin panel and delete carlos user.

# Ingrediants : Same as above

# Solving : 

- Let's try to login using the exploit server mail id.

<img width="1244" height="462" alt="image" src="https://github.com/user-attachments/assets/135ec49c-2cb8-4023-9b69-9fbb3f7d0156" />

- Unlike the last lab last it doesn't have the update email hence we can't update the email to dontwannacry domain. Hence we will try to add the huge character and see what happens. We will try to add the characters before that.

<img width="1333" height="650" alt="image" src="https://github.com/user-attachments/assets/a7c351b8-7616-4e4e-bac6-45ddfd265e7f" />

- It result like the following.

<img width="1291" height="587" alt="image" src="https://github.com/user-attachments/assets/1f364d99-3dd4-4f4e-9041-0e5c76e7b49d" />

- Let's register and see the result.

<img width="1260" height="490" alt="image" src="https://github.com/user-attachments/assets/b5e577d9-e4f6-43a9-90a1-5edafd59951e" />

- We can't see the exploitserver.net portion only AAAA is tere. It is truncating some portion of the email.

<img width="1221" height="479" alt="image" src="https://github.com/user-attachments/assets/cfd7b2d5-73d7-4708-9964-11b00791a3a2" />

- When counting we can notice that notice it is allowing only 256 characters. Hence let's add like the following.

AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA@dontwannacry.com%40exploit-0a5f00f4042c1f6382d550d0015700f0.exploit-server.net

<img width="1258" height="498" alt="image" src="https://github.com/user-attachments/assets/8b07a579-b455-4f83-9690-ec1ea94d1e45" />

- Hence we can see the admin panel here. Hence by detelting the carlos user we can solve the lab.

<img width="1127" height="495" alt="image" src="https://github.com/user-attachments/assets/67a4348b-fba1-4b89-9f34-d89d9fd50bd6" />


# ------------------------------------------------------------------------------


# 7. Weak isolation on dual-use endpoint.

<img width="790" height="183" alt="image" src="https://github.com/user-attachments/assets/e4c5bb59-0537-49e2-ab1e-bfd81160815b" />

# Goal : Access the admin panel and delete carlos user.

# Ingrediants : Same as above

# Solving : 

- Let's login and see the response. We can able to see there is a current password and new password menu where we can update the password.

<img width="1158" height="711" alt="image" src="https://github.com/user-attachments/assets/db86a178-8629-43af-a073-2f4448f47005" />

- When we fuzz the admin username in the url we got a response in the UI like "Admin interface only available if logged in as an administrator". 

<img width="1098" height="416" alt="image" src="https://github.com/user-attachments/assets/fa0e1096-0cf1-485c-89e7-f819854bd7dd" />

- Let's try to change the username and see the response. It says current password is incorrect 

<img width="1132" height="552" alt="image" src="https://github.com/user-attachments/assets/e255b7da-a5cd-42db-b584-9c294386aa88" />

- let's remove the current-password and see if it is still working. We can see it worked and password changes successfully.

<img width="1262" height="488" alt="image" src="https://github.com/user-attachments/assets/7829cefb-e802-4630-ba3a-58c001f0ebbf" />

- Hence login as administrator, access the admin panel and delete the carlos user.

<img width="1252" height="532" alt="image" src="https://github.com/user-attachments/assets/73ad4458-ecf0-4f40-8abc-33e0f20dd528" />

<img width="1248" height="443" alt="image" src="https://github.com/user-attachments/assets/2f5c2141-c6c3-45f2-a43d-912d244bb61e" />


# ------------------------------------------------------------------------------


# 8. Insufficient workflow validation.

<img width="747" height="132" alt="image" src="https://github.com/user-attachments/assets/a51f7954-5421-417e-8650-05c228452b8b" />

# Goal : Same as above

# Ingrediants : Same as above

# Solving : 

- Let's login and add the leather to the cart and see the response.

<img width="1189" height="554" alt="image" src="https://github.com/user-attachments/assets/c57d5590-1a28-4612-b9ac-6629f3fa3f8b" />

- Lets say we have tried all the possibilities of previous labs and nothing is working out. Hence we will try to buy an item which we can afford and see the response.

<img width="1056" height="402" alt="image" src="https://github.com/user-attachments/assets/deaefa06-5ac3-4a44-a51b-494fc6c5a49a" />

- We got 2 response post and get confirmation. post is only taking the csrf token nothing more than 

<img width="1110" height="521" alt="image" src="https://github.com/user-attachments/assets/2bdd988c-f28f-4da8-8075-ba1cb59d8824" />

- In the get reuqest we got a confirmation=true if it has a flaw it will to exploited if confirmation=true. 

<img width="1094" height="485" alt="image" src="https://github.com/user-attachments/assets/991c4c3a-e375-405c-bfc3-faa451befdad" />

- Hence we will try to add the leather jacket to the cart and send this request. Therefor we solved the lab.

<img width="1221" height="609" alt="image" src="https://github.com/user-attachments/assets/8480b239-1574-4813-8ec0-fda01d70a428" />

# ------------------------------------------------------------------------------


# 9. Authentication bypass via flawed state machine.

<img width="762" height="165" alt="image" src="https://github.com/user-attachments/assets/dc1f0d40-1186-453f-a37d-e3cc1cbd5b58" />

# Goal : Access the admin panel and delete carlos user.

# Ingrediants : Same as above

# Solving : 

- Let's login and see the response. We can it having a role selector page we have to select user or content author. Lets login as both and see any difference in the UI.

- As a user nothing is different.

  <img width="1196" height="532" alt="image" src="https://github.com/user-attachments/assets/8ab27764-b4a1-4e0d-8ed2-7a9544b02389" />

- As a content author nothing is different.

  <img width="1207" height="507" alt="image" src="https://github.com/user-attachments/assets/31e47d31-271a-43a1-9335-d36ae0564528" />

- We will try to drop the role selector request by intercepting the request.

<img width="1113" height="644" alt="image" src="https://github.com/user-attachments/assets/bcb0b13a-0e98-4838-a531-1c4f93239dc2" />

- Since no roles are selected we can see admin panel there. 

<img width="1295" height="529" alt="image" src="https://github.com/user-attachments/assets/79f7ff17-8565-4854-97b7-20b585a3bd68" />

- Hence deleting the carlos user we can solve the lab.

<img width="1225" height="503" alt="image" src="https://github.com/user-attachments/assets/1779d9e8-7a43-4a6b-b9b3-d9a6cfa1e44c" />

# ------------------------------------------------------------------------------
  



