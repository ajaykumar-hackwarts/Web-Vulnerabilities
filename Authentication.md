Authentication : Checking the person is really who they claim to be.

# 1. Username enumeration via different responses.

<img width="745" height="259" alt="image" src="https://github.com/user-attachments/assets/37b66a9c-787b-4786-a401-aabf57cca466" />

# Goal : To enumerate the valid username and brute force the password access the account page. 

# Ingrediants : Home, My account 

# Solving : 

- We will try to login with the dummy credentials and see the response. 

<img width="875" height="379" alt="image" src="https://github.com/user-attachments/assets/ca73f919-3960-440a-b2be-10009c6cffe3" />

- It sends the value in the post request.

<img width="1248" height="498" alt="image" src="https://github.com/user-attachments/assets/32a20222-03f2-40ff-8b01-a690eabf8d85" />

- We will send the request to the intruder and try to brute force the username and password with the given list using the cluster bomb feature

<img width="1361" height="610" alt="image" src="https://github.com/user-attachments/assets/37700eba-8588-466b-8831-fe3e85229e35" />

- We got one response which is different in length and 302 response. 

<img width="1305" height="546" alt="image" src="https://github.com/user-attachments/assets/6f342d40-3f1d-49d6-ba89-6719395788d4" />

- When we tried that credentials we successfully solved the lab.

<img width="1306" height="582" alt="image" src="https://github.com/user-attachments/assets/af3206f3-8d68-420c-823c-27beb1188daf" />

# ------------------------------------------------------------------------------

# 2. 2FA simple bypass.

<img width="774" height="192" alt="image" src="https://github.com/user-attachments/assets/7badb2c9-0240-47ce-ae7b-fdc8215700fc" />

# Goal : To access carlos account page. 

# Ingrediants : Home, My account and email client. 

# Solving : 

- Firstly we will login as wiener and peter. We can see since it has 2 factor authentication we need a code to solve complete login.

<img width="1186" height="423" alt="image" src="https://github.com/user-attachments/assets/01f9f0b3-fd31-479c-b0bc-00a76eb30d16" />

- The verification should be available in the email client.

<img width="1270" height="591" alt="image" src="https://github.com/user-attachments/assets/668998a8-3ef7-4f40-82bd-933e5a485865" />

<img width="1197" height="552" alt="image" src="https://github.com/user-attachments/assets/0824be01-f740-40c7-a0d2-1731f09085c1" />

- Now we will see the two responses.

<img width="1101" height="501" alt="image" src="https://github.com/user-attachments/assets/4f7cb40e-7177-4e8d-b8e9-d52579b319ce" />

- We will try to intercept the request of carlos login request and forward the post request. 

<img width="1032" height="553" alt="image" src="https://github.com/user-attachments/assets/c9cb8b4f-9abe-4bb1-bb0d-968eb10e5244" />

<img width="1151" height="601" alt="image" src="https://github.com/user-attachments/assets/3dba5063-fd9c-464e-b52e-c777fc1ce2d3" />

- When we forward it we can notice that it is going for the next page for verification submit code. 

<img width="1274" height="561" alt="image" src="https://github.com/user-attachments/assets/692bf62b-d4bd-4c87-a9be-aeed7d4b6dfc" />

- We will drop(delete the request to the server) the request and see that we can still login to my-account page.

<img width="1195" height="478" alt="image" src="https://github.com/user-attachments/assets/82077ca9-c917-47cf-ba2a-593b00c3d8a6" />

- And we can see we successfully bypassed the 2FA and solved the lab.

<img width="1294" height="576" alt="image" src="https://github.com/user-attachments/assets/34708249-0ee3-4241-8c46-e3d5afe9ae7d" />
  
# ------------------------------------------------------------------------------

# 3. Password reset broken logic.

# Goal : To access carlos account page. 

# Ingrediants : Home, My account and email client. 

<img width="1035" height="592" alt="image" src="https://github.com/user-attachments/assets/23148dd8-d19e-40eb-a199-d65406c87b54" />

# Solving : 

- To reset carlos's password then login and access the "My-account" page.




# ------------------------------------------------------------------------------

# 4. Username enumeration via subtly different responses

<img width="779" height="259" alt="image" src="https://github.com/user-attachments/assets/86a84fd7-5918-4994-80c8-a910729db8b3" />

# Goal : To enumerate the valid username and brute force the password access the account page.  

# Ingrediants : Home, My account and email client. 

# Solving : 

- Firstly we will login as wiener and peter and see the response.

<img width="1350" height="521" alt="image" src="https://github.com/user-attachments/assets/64b2d8da-be5e-492c-89ac-f848db905d63" />

- Let's try to brute force the username with the given list and see the difference in the response.

<img width="1144" height="627" alt="image" src="https://github.com/user-attachments/assets/518cb1e7-a95a-4f23-b1fa-225e3d2dd257" />

- Since we got almost same response we will search the exact words in the reponse and in put it in the filter do a negative search.

<img width="1215" height="562" alt="image" src="https://github.com/user-attachments/assets/d50470c0-0060-4df1-8185-f1eae3ca115a" />

- And we got only one response which doesn't have the exact words. A dot . is missing. So we can say if the username is correct and password is wrong the response would be "Invalid username or password".  

<img width="1171" height="566" alt="image" src="https://github.com/user-attachments/assets/fc3fd433-e9e3-45c1-8941-f05cf123f14f" />

- Now we will enumerate the password with the correct username. We got a 302 reponse

<img width="1357" height="605" alt="image" src="https://github.com/user-attachments/assets/48c11070-beba-4e54-9758-9496e32dd334" />

- When we tried to with these credentials we solved the lab successfully.

<img width="1149" height="544" alt="image" src="https://github.com/user-attachments/assets/a5e2c8fe-4df2-4507-830f-a5f4587d8360" />

<img width="1132" height="565" alt="image" src="https://github.com/user-attachments/assets/61adc3b4-7c62-4250-811d-6728a47a3011" />

# ------------------------------------------------------------------------------


# 5. 
