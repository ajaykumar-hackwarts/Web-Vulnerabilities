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

Username enumeration via subtly different responses

