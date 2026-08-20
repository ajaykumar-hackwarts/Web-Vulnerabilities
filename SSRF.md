# Server Side Request Forgery(SSRF) : An attack where an attacker tricks the website's server into making requests to a destination chosen by attacker which is internal or restricted access. 


# 1. Basic SSRF against the local server. 

<img width="804" height="118" alt="image" src="https://github.com/user-attachments/assets/de43ba68-1719-40f9-bbb9-9dd006604e4f" />

# Goal : To change the stock check url to access admin interface and delete carlos user. 

# Ingrediants : Home, My account, view details. 
 
# Solving : 

- Lets check the stock and see the response.

<img width="1110" height="586" alt="image" src="https://github.com/user-attachments/assets/1cae3c60-f579-42cc-bf03-ac9f5fa4f634" />

<img width="955" height="540" alt="image" src="https://github.com/user-attachments/assets/17281786-bb80-4462-9ef7-38e6e2412190" />

- Let's change the stockapi url to localhost url and check it gives the positive response.

<img width="1055" height="534" alt="image" src="https://github.com/user-attachments/assets/7ab07e8a-3908-48f0-ad9e-f4eacd65b263" />

<img width="1074" height="453" alt="image" src="https://github.com/user-attachments/assets/7c49cdac-257b-414e-91b0-f26322d969d7" />

- Hence let's delete the carlos user and solve the lab.

<img width="1035" height="497" alt="image" src="https://github.com/user-attachments/assets/4591ad6b-aba4-4157-a11d-5b9d497630a3" />

<img width="1248" height="503" alt="image" src="https://github.com/user-attachments/assets/7d257251-6efd-4714-b751-932f5baefa23" />

# ------------------------------------------------------------------------------


# 2. Basic SSRF against another back-end system. 

<img width="727" height="114" alt="image" src="https://github.com/user-attachments/assets/c3165bac-7f4b-42b9-a5d1-d4ff28030f02" />

# Goal : To use the stock check feature to scan the internal 192.168.0.X range for an admin interface on port 8080 and delete carlos user. 

# Ingrediants : Home, My account, view details. 
 
# Solving : 

- Lets check the stock and see the response.

<img width="1034" height="535" alt="image" src="https://github.com/user-attachments/assets/9235aa99-fc9d-4305-a0a6-79cdde067716" />

- Let's try to change the value and see the response.

<img width="1271" height="522" alt="image" src="https://github.com/user-attachments/assets/b4d09dbe-75b3-4d64-838a-473d751c555b" />

- Still the same output hence we will use intruder to send many requests. 

<img width="1125" height="493" alt="image" src="https://github.com/user-attachments/assets/73a6e7ee-daea-4373-87a6-a4225f99f544" />

- 183 only gives different output.

<img width="1148" height="573" alt="image" src="https://github.com/user-attachments/assets/76995741-92a6-4e57-a22b-9c1a3e069c9c" />

- Hence by deleting the carlos user we can solve the lab. 

<img width="1117" height="477" alt="image" src="https://github.com/user-attachments/assets/700fa3a3-ef8e-4ef6-9a38-b648e6b9b6bd" />

<img width="1019" height="513" alt="image" src="https://github.com/user-attachments/assets/e1713da6-4b9f-4c12-8a80-f4c8904fa95a" />

<img width="1230" height="552" alt="image" src="https://github.com/user-attachments/assets/c625dbfd-a85e-4abc-9036-534a34195b4b" />

# ------------------------------------------------------------------------------


# 3. Blind SSRF with out-of-band detection.

<img width="728" height="140" alt="image" src="https://github.com/user-attachments/assets/28c93256-9181-4300-b9df-4654f59f313b" />

# Goal : To make a http request to burp colloborator server. 

# Ingrediants : Home, My account, view details. 
 
# Solving : 

- Lets view the details and see the response and we can notice that it has a referrer for the analytical purpose. 

<img width="1241" height="519" alt="image" src="https://github.com/user-attachments/assets/0905f21f-5c66-4640-a169-98175abab6bc" />

- Let's change the refferer header url to the burp collobrator url and see we getting the response externally. 

<img width="1224" height="481" alt="image" src="https://github.com/user-attachments/assets/432d7266-ad89-4f57-b177-3beddaca2749" />

- We can see it is sending the request externally and it is captured in the collaborator. And we solved the lab. 

<img width="1280" height="570" alt="image" src="https://github.com/user-attachments/assets/9400c4a9-0397-47a9-87a9-5b90f2c0c154" />

<img width="1295" height="573" alt="image" src="https://github.com/user-attachments/assets/caf8ccc1-4c35-49ca-9968-063d1049521e" />

# ------------------------------------------------------------------------------

# 4. 
