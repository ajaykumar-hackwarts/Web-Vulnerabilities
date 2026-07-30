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

<img width="1071" height="656" alt="image" src="https://github.com/user-attachments/assets/8d84e74b-0598-4109-81a1-44c6e6a60c9e" />

- We will see the response and try to see the password and we got the password value. 

<img width="1105" height="548" alt="image" src="https://github.com/user-attachments/assets/5a37aada-8523-4173-a20a-7a9dd1c28c16" />

- We login as the administartor. 

<img width="1289" height="596" alt="image" src="https://github.com/user-attachments/assets/c757c447-a3b2-4f70-9203-fb568802825d" />

- And by deleting the carlos user we solve the lab. 

<img width="1279" height="479" alt="image" src="https://github.com/user-attachments/assets/bcc1c360-0901-412f-b616-ecbb61bef824" />

 # ------------------------------------------------------------------------------

 # 9. Insecure direct object references. 

## Goal : To find the password of carlos user and login. 

## Ingrediants : Same as above and live chat button is extra. 

## Solving :

- Since it has the live chat we will play with that and see the response and click on the view transcript button.

<img width="1240" height="535" alt="image" src="https://github.com/user-attachments/assets/b3a00476-4846-47fa-a7e9-51ea263a2163" />

<img width="1075" height="429" alt="image" src="https://github.com/user-attachments/assets/b6605aa6-3f0a-4532-95f4-7ee0be932b41" />

- It is downloading a txt file when clicking the transript in the history it has the chat history. Since it is 2.txt there must bu 1.txt we will try to check that.

<img width="1245" height="515" alt="image" src="https://github.com/user-attachments/assets/c3fb59be-5eb8-4ef9-a91b-f8818d7975cc" />

- And Here we go we got the password in the chat history hence by submiting it we can solve the lab. 

<img width="1361" height="509" alt="image" src="https://github.com/user-attachments/assets/79b5329e-64e6-40d8-a8ca-3bfb30753617" />

 # ------------------------------------------------------------------------------

 # 10. URL-based access control can be circumvented. 

 <img width="803" height="157" alt="image" src="https://github.com/user-attachments/assets/5f6a8f46-6cd6-4363-b5ae-698b163a452a" />

## Goal : To access the admin panel and delete the carlos user.  

## Ingrediants : Same as before. 

## Solving :

- Lets try to click on the admin panel and see the response.

<img width="1313" height="610" alt="image" src="https://github.com/user-attachments/assets/67202f2e-2773-444d-981f-1f901901999a" />

<img width="1061" height="397" alt="image" src="https://github.com/user-attachments/assets/cc282022-f0f4-448f-93f6-67578a460eaf" />

- It is giving the access denied 403 forbidden response.

<img width="1070" height="505" alt="image" src="https://github.com/user-attachments/assets/3a1a2f4a-4c4e-4c72-9f81-f63834f18ee6" />

- Let's add a random X-origin value and see the response. Surprisingly it is not saying forbidden it is saying not found. 

<img width="1007" height="547" alt="image" src="https://github.com/user-attachments/assets/eddea6ec-48a3-4228-b72c-4f5a73e0ca41" />

- Lets give the admin value instead of random value and see the response. We can see It gives the admin panel 

<img width="1207" height="563" alt="image" src="https://github.com/user-attachments/assets/27bed568-fabf-4f08-9d4b-ced15d5ea058" />

- Let's test that in browser and see the result 

<img width="1319" height="455" alt="image" src="https://github.com/user-attachments/assets/a177c17d-ae83-4e67-b71e-d9f4c59cbd05" />

- When we tried to delete the carlos user it is not deleting. 

<img width="1047" height="411" alt="image" src="https://github.com/user-attachments/assets/11159f47-efab-435f-82dc-d859f52f2103" />

- Hence we will try to paste and send the entire url and see the response

<img width="1088" height="558" alt="image" src="https://github.com/user-attachments/assets/bb39ae38-0282-4c44-a62e-e0c9cb65184b" />

- We can see we successfully completed the lab.

<img width="1162" height="525" alt="image" src="https://github.com/user-attachments/assets/159b548b-2c36-42a9-91d4-9648306a323b" />

 # ------------------------------------------------------------------------------


 # 11. Method-based access control can be circumvented. 

 <img width="762" height="183" alt="image" src="https://github.com/user-attachments/assets/4e6ba8a0-3d90-49ed-99b3-2b0ccdfbfdd0" />

## Goal : To exploit flawed access control and became the admin user. 

## Ingrediants : Same as before. 

## Solving :

- As given in the lab we will login as administrator. We will click on the admin panel 

<img width="1286" height="520" alt="image" src="https://github.com/user-attachments/assets/04e3bc59-da6f-4218-81c2-17a0173728da" />

- We can see in the admin panel it has 2 button upgrade and downgrade.

<img width="1306" height="396" alt="image" src="https://github.com/user-attachments/assets/732c59ef-b321-4731-9164-10e32043e72e" />

- When we click upgrade it upgraded as admin.

<img width="1038" height="318" alt="image" src="https://github.com/user-attachments/assets/d394f0f5-995c-4e47-ac45-e150680e1d1f" />

- When we click downgrade it becomes normal user.

<img width="1119" height="364" alt="image" src="https://github.com/user-attachments/assets/6268243e-8546-469a-b7c3-6e16403bfee3" />
 
- When we see the response of the adnin. 

<img width="883" height="509" alt="image" src="https://github.com/user-attachments/assets/e6eaf654-71fd-4b08-a1ca-f616f4ed1550" />

- No we will try to login as wiener and peter and will see the response.

<img width="1290" height="500" alt="image" src="https://github.com/user-attachments/assets/a9e3c8e1-95bd-42e8-8b35-3ec2bc44f52e" />

<img width="1072" height="567" alt="image" src="https://github.com/user-attachments/assets/9cf3bf28-869e-482f-9f25-79e9fe29bd9d" />

- Now we will put this session to the admin request. We can notice it gives the response as Unauthorized. 

<img width="1016" height="557" alt="image" src="https://github.com/user-attachments/assets/0c06d924-503b-453f-ae43-d14c0586650f" />

- We will try to change the method type and change the user to our user wiener and check the response.

<img width="528" height="531" alt="image" src="https://github.com/user-attachments/assets/2a3c66ca-2a69-4176-ad85-9b66416c9d0b" />

- We got a positive 302 response and we solved the lab successfully. 

<img width="1005" height="531" alt="image" src="https://github.com/user-attachments/assets/eaef2177-627d-445b-a59d-29dde20cfd81" />

<img width="1195" height="527" alt="image" src="https://github.com/user-attachments/assets/66ea07f6-09e7-4067-a498-17915019680a" />

 # ------------------------------------------------------------------------------



