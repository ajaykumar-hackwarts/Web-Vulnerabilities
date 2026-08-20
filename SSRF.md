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

# 4. SSRF with blacklist-based input filter. 

<img width="819" height="171" alt="image" src="https://github.com/user-attachments/assets/339471d1-f1b4-4b24-9767-4bf1fa636376" />

# Goal :  To use the stock check feature to scan the internal 192.168.0.X range for an admin interface on port 8080 and delete carlos user. 

# Ingrediants : Home, My account, view details. 
 
# Solving : 

- Lets check the stock and see the response.

<img width="1305" height="484" alt="image" src="https://github.com/user-attachments/assets/bbe8f5c6-206d-43d3-a295-262bb8fc9549" />

- Lets change it to local host and see the response. And it shows a 400 error it is restricts some strings like localhost. 

<img width="1364" height="481" alt="image" src="https://github.com/user-attachments/assets/a33b7a03-3be9-4d60-b72e-d1e7798d917b" />

- Also it restricting the ip address of local host.

<img width="1265" height="564" alt="image" src="https://github.com/user-attachments/assets/a9a9a483-4775-484a-934a-4b27f5458573" />

<img width="1320" height="584" alt="image" src="https://github.com/user-attachments/assets/078e6572-05f1-4513-b38f-538e992343e4" />

- And it has the admin panel.

<img width="1365" height="631" alt="image" src="https://github.com/user-attachments/assets/53be448a-d026-4305-afba-ce05bf1ac452" />

- Let's try to access the admin panel using the admin at the end. It is also restricting the word admin

<img width="1334" height="501" alt="image" src="https://github.com/user-attachments/assets/1233c106-f008-4ccd-b9be-5caff734d3fd" />

- Let's try to encode that and see the response. It is url decoding it and searching the restricted word is there or not. 

<img width="1352" height="535" alt="image" src="https://github.com/user-attachments/assets/2894cd04-b901-4ad2-a482-34026b1f83f4" />

- Let's encode it one more time and see the response. We got the postive response 

<img width="1299" height="604" alt="image" src="https://github.com/user-attachments/assets/d1f09eef-42fd-40f0-979a-fbbb889ec517" />

- Hence we can notice that it is url encoding only one time

<img width="1188" height="578" alt="image" src="https://github.com/user-attachments/assets/9f008e3c-84d9-4af7-ae2b-610e7d1bfab0" />

- Hence by deleting the carlos user we solved the lab. 

<img width="1273" height="525" alt="image" src="https://github.com/user-attachments/assets/6109d1cb-3915-483f-a263-6b9649c15ae0" />

<img width="1235" height="543" alt="image" src="https://github.com/user-attachments/assets/83ccb02a-2c94-451c-b4a5-a74f777710bb" />

# ------------------------------------------------------------------------------
