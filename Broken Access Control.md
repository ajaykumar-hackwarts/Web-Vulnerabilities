# Access control vulnerabilities : It's a vulnerbility where application is fails to properly enforce the authorization rules, allowing user to access or perform action that they are not permitted to do it. 

# 1. Unprotected admin functionality. 

<img width="413" height="99" alt="image" src="https://github.com/user-attachments/assets/9cf0591b-7294-48fe-93db-525182f61be2" />

# Goal : To delete the carlos user. 

# Ingrediants : Home, My account, view details. 

<img width="1259" height="559" alt="image" src="https://github.com/user-attachments/assets/666fbd07-6aeb-4d5c-ad0d-ab8463cd17f8" />

# Solving : 

- Firstly we will try to brute force to enter the admin panel.

<img width="1209" height="561" alt="image" src="https://github.com/user-attachments/assets/fc3672a0-ff0a-4a68-83f0-0ea5720dc491" />

<img width="1184" height="415" alt="image" src="https://github.com/user-attachments/assets/e884ed2f-39bd-4262-9c14-62fddb667865" />

<img width="1119" height="422" alt="image" src="https://github.com/user-attachments/assets/5c86bd62-5811-42ab-9c5b-d1651e747f05" />

- Hence we can able to access the admin panel because of poor access control rules.  
 
<img width="1345" height="474" alt="image" src="https://github.com/user-attachments/assets/30e24861-00a4-4926-a22f-f7165129eb0e" />

- Hence by deleting the carlos user we solve the lab.

<img width="1228" height="488" alt="image" src="https://github.com/user-attachments/assets/59b0cb91-cbfa-41ba-80d5-1aa8ce5ed542" />

# ------------------------------------------------------------------------------


# 2. Unprotected admin functionality with unpredictable URL. 

<img width="769" height="120" alt="image" src="https://github.com/user-attachments/assets/b4f092e7-6074-4404-a441-59fa7c3ac065" />

## Goal : To delete the carlos user. 

## Ingrediants : Same as above. 

## Solving : 

- First we will try the robots.txt file.

- It is a file that tells search engine bots which should or should not crawl. Crawling is viewing, reading and follwing the link automatically.

<img width="1180" height="474" alt="image" src="https://github.com/user-attachments/assets/931d198c-6b5d-473b-8a24-045fa00ebfe0" />
 
- Since there isn't one we will see the page source. We got the script which has the admin directory. /admin-un2vic

<img width="1016" height="631" alt="image" src="https://github.com/user-attachments/assets/db13c1cb-d954-4be2-b941-ce0ae9b6891c" />

<img width="1147" height="542" alt="image" src="https://github.com/user-attachments/assets/7e6c5054-3d01-46fa-a479-8ce14d70f026" />

- It worked and by deleting the carlos user we solved the lab.

<img width="1209" height="574" alt="image" src="https://github.com/user-attachments/assets/8a4c033d-5c63-4768-9845-49e7b9f9d688" />

# ------------------------------------------------------------------------------


# 3. User role controlled by request parameter. 

<img width="770" height="163" alt="image" src="https://github.com/user-attachments/assets/5d5f8d75-51b6-40da-aceb-639652edb134" />

## Goal : To delete the carlos user. 

## Ingrediants : Same as above. 

## Solving : 

- Let's login using the credentials and see the response.

<img width="1298" height="537" alt="image" src="https://github.com/user-attachments/assets/06841e3d-ad25-41d7-857c-92bd7d8c4199" />

- We can see a strange parameter in the request that is admin=false 

<img width="1304" height="556" alt="image" src="https://github.com/user-attachments/assets/e3fa67dc-5a22-4e73-9544-eeecc0978d3d" />

- We will try to set it true and see the change in the response and we can notice we got the admin panel in teh response.  

<img width="1228" height="526" alt="image" src="https://github.com/user-attachments/assets/af587c2d-d0b5-4640-91bb-139db6e22733" />

- Let's try to change this in the browser.

<img width="1347" height="609" alt="image" src="https://github.com/user-attachments/assets/19ec0b9a-212a-4d85-927d-3684a37c78ca" />

<img width="1350" height="552" alt="image" src="https://github.com/user-attachments/assets/326f3aed-6c5a-4b78-a33c-f044d993442f" />

- We got the admin panel and by deleting the carlos user we solve the lab. 

<img width="1319" height="422" alt="image" src="https://github.com/user-attachments/assets/48a31044-6ca8-4172-af1f-301e8d54a822" />

<img width="1238" height="455" alt="image" src="https://github.com/user-attachments/assets/3ecefe76-070d-4ba2-8d93-4d27fb3c0019" />

 # ------------------------------------------------------------------------------

# 4. User role can be modified in user profile. 

<img width="758" height="178" alt="image" src="https://github.com/user-attachments/assets/3dd463c9-b599-4f9e-8f5b-4c6262ee6949" />

## Goal : To delete the carlos user. 

## Ingrediants : Same as above. 

## Solving : 

- Let's login using the credentials and see the response.

<img width="1296" height="573" alt="image" src="https://github.com/user-attachments/assets/74e1a62d-1b53-46dc-9bdd-1b0692686b1c" />

<img width="1090" height="537" alt="image" src="https://github.com/user-attachments/assets/3221dac2-1168-4afb-b695-3b21fe8c83cd" />

- Let's try to change the id to admin and see the reponse.

<img width="997" height="535" alt="image" src="https://github.com/user-attachments/assets/9324b95a-abf6-4ecc-9be9-78c41a6a0542" />

<img width="1145" height="603" alt="image" src="https://github.com/user-attachments/assets/ea5b6bc8-5e63-4759-aa17-3b7be8f816b2" />

<img width="1145" height="597" alt="image" src="https://github.com/user-attachments/assets/fa575b57-8690-430b-a2f8-35d543135d12" />

- When changing the id we can't able to find the admin related strings in the response. Hence we will try to update the email and see the response.

<img width="1237" height="571" alt="image" src="https://github.com/user-attachments/assets/bb596df5-4487-4d93-9de9-bc43900f206f" />

- We can see in the change email it has the 4 parameter id email, name and apikey in the response and has only email parameter in request we will try to add the id and change it to 2 in the request.

<img width="1265" height="602" alt="image" src="https://github.com/user-attachments/assets/4079cd89-9892-4619-9260-21d9263df293" />

- We can see it is changed and we have the admin panel in the response.

<img width="1147" height="590" alt="image" src="https://github.com/user-attachments/assets/10323d6f-1ace-4ce5-b594-90f409122d48" />

- Hence by deleting the carlos user in the admin panel we solve the lab.

<img width="1314" height="469" alt="image" src="https://github.com/user-attachments/assets/38de0bfd-f439-4570-ba25-019fc3690efb" />

 # ------------------------------------------------------------------------------

# 5. User ID controlled by request parameter. 

<img width="717" height="130" alt="image" src="https://github.com/user-attachments/assets/d1eab210-69ec-4268-92a3-0d66739741fa" />

## Goal : To optain the api key from the carlos and submit it. 

## Ingrediants : Same as above. 

## Solving : 

- Like the usual we will try to login as wiener and see the response.

<img width="1124" height="575" alt="image" src="https://github.com/user-attachments/assets/09199f98-ad78-4a1c-ab8b-17dc35f3637d" />

- Let's change the user ID and see the response. Hence by changing the user id in the request parameter we got the api key

<img width="1164" height="590" alt="image" src="https://github.com/user-attachments/assets/d5c1a7e0-53d3-4321-aaf8-d9181c2f857f" />

- We will submit the api key and solve the lab.

<img width="1107" height="521" alt="image" src="https://github.com/user-attachments/assets/10d2679d-28c0-44c7-bdb3-3b3fec0355ca" />

 # ------------------------------------------------------------------------------

 # 6.  User ID controlled by request parameter, with unpredictable user IDs. 

<img width="785" height="172" alt="image" src="https://github.com/user-attachments/assets/8aa2e33a-7453-4532-9cb4-ce40e91c8cff" />

## Goal : To find the GUID from carlos and submit the api key. 

## Ingrediants : Home, my-account, view post and submit solution. 

## Solving : 

- We will start like last lab. We can notice something different in the request as instead of it is having the id=wiener it has random numbers which is GUID(Global user ID)

<img width="1210" height="587" alt="image" src="https://github.com/user-attachments/assets/658fb67f-095d-40c8-a886-5ed25e1bfa66" />

- We will try to find the carlos's user ID. By viewing all the buttons.

<img width="1019" height="563" alt="image" src="https://github.com/user-attachments/assets/d20ea023-e29e-42f7-8275-2bf61b48198e" />

 <img width="1215" height="507" alt="image" src="https://github.com/user-attachments/assets/2ab43f49-c81c-40a5-a02d-ff9505aa2a6e" />

- By clicking on the carlos we got an user ID of carlos in the request.

<img width="1365" height="542" alt="image" src="https://github.com/user-attachments/assets/2b5989d2-b0f2-4170-947f-b63054f527da" />

- We will send that GUID in the id place and get the api key.

<img width="1099" height="577" alt="image" src="https://github.com/user-attachments/assets/5e8f98ae-c40b-4d79-a3e0-4012acda2acd" />

- By submitting the api key we solved the lab.

<img width="1208" height="561" alt="image" src="https://github.com/user-attachments/assets/9974796d-e575-4af7-9fda-daee6dca6090" />

 # ------------------------------------------------------------------------------

 # 7. User ID controlled by request parameter with data leakage in redirect. 

<img width="753" height="168" alt="image" src="https://github.com/user-attachments/assets/1fd2c180-d6a1-4de5-abd0-28bffd472c7c" />
 
## Goal : To find the GUID from carlos and submit the api key. 

## Ingrediants : Same as above. 

## Solving : 

- We login and we will try to change the user id. 

<img width="1277" height="528" alt="image" src="https://github.com/user-attachments/assets/2d7589e2-cb2a-48b6-8a44-4c07dcf0d1e2" />

<img width="1317" height="645" alt="image" src="https://github.com/user-attachments/assets/64492889-6f40-4600-9852-9eaa0d2d7409" />

- We can see it redirects to the login page. 

<img width="1351" height="638" alt="image" src="https://github.com/user-attachments/assets/12e5e510-7276-41cc-82a8-34954edf6c21" />

- But in the redirection response it gives all the information we want especially the api key. 

<img width="1291" height="600" alt="image" src="https://github.com/user-attachments/assets/4ad40604-130f-4647-bd82-0d6d140a8f09" />

- Hence by submitting the api key we will solve the lab.

<img width="1176" height="581" alt="image" src="https://github.com/user-attachments/assets/a7af3b67-01d7-4494-bc7b-567a8490e46c" />

 # ------------------------------------------------------------------------------

 # 8. User ID controlled by request parameter with password disclosure. 

<img width="779" height="194" alt="image" src="https://github.com/user-attachments/assets/56bc3862-03e3-468e-b28c-db59b17e1857" />

## Goal : To retrive the admin's password and delete the carlos user. 

## Ingrediants : Same as above. 

## Solving :

- We login and we can notice it has the update password button and box which has password place holder in it. This is a poorly contructed UI and website which reveals password. 

<img width="1298" height="557" alt="image" src="https://github.com/user-attachments/assets/1e6a2116-acd1-4ecc-a21a-d1b337ccf61e" />
 
- We will try to change the ID as administrator and see the response. We can able to get to login as an administrator. 

<img width="1249" height="668" alt="image" src="https://github.com/user-attachments/assets/a1dd3410-949b-44dd-b0d6-f3678597def5" />

- Now we will update the password.

