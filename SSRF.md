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


# 5.  SSRF with filter bypass via open redirection vulnerability.

<img width="760" height="195" alt="image" src="https://github.com/user-attachments/assets/c2c1c4a7-09b1-4235-a66e-4d09fbafc5b0" />

# Goal :  To use the stock check feature to scan the internal 192.168.0.X range for an admin interface on port 8080 and delete carlos user. 

# Ingrediants : Home, My account, view details. 
 
# Solving : 

- Lets check the stock and see the response. We can notice that there is an extra button called next product which will do the redirection lets send this response too.  

<img width="1260" height="575" alt="image" src="https://github.com/user-attachments/assets/b8923d75-4bbc-432d-8d9a-4f7c90c68d94" />

<img width="1285" height="502" alt="image" src="https://github.com/user-attachments/assets/ea4d54fe-9159-403e-ac88-a8975d7eb6d6" />

<img width="1269" height="501" alt="image" src="https://github.com/user-attachments/assets/0406da10-0564-452a-ab36-9bafe39d4880" />

- When we follow the redirection it is going to the page whatever we given in the path attribute. 

<img width="1187" height="398" alt="image" src="https://github.com/user-attachments/assets/91a45538-83b7-4e09-a50a-52eb118538ef" />

- Lets change the stockapi value to access the admin panel and see the response and we can confirm that it is restricted. 

<img width="1204" height="540" alt="image" src="https://github.com/user-attachments/assets/1c9be15b-0e06-4511-aacb-1cb65c359403" />

- We can notice that whatever we give in the path it is redirecting to that page.

 <img width="1217" height="460" alt="image" src="https://github.com/user-attachments/assets/935ba523-6339-4e6d-bcdc-f15a4ca7ba4b" />

<img width="1130" height="483" alt="image" src="https://github.com/user-attachments/assets/45509e6b-bc3d-44d1-bd74-a5f9f54f3715" />

- Hence we will use the redirection path here in check stock and see the response. We can able to access the admin panel. 

<img width="1364" height="545" alt="image" src="https://github.com/user-attachments/assets/70fed89c-c1e0-4522-95a9-6015c560dbfd" />

- Hence by deleting the carlos user we solved the lab.

<img width="1319" height="539" alt="image" src="https://github.com/user-attachments/assets/1e19b6ae-d441-4b8f-ae18-ba198ceaad28" />

<img width="1227" height="581" alt="image" src="https://github.com/user-attachments/assets/133ee57f-af9d-4f58-bfe7-11ee646fb873" />


# ------------------------------------------------------------------------------

# 6. Blind SSRF with Shellshock exploitation.

<img width="750" height="176" alt="image" src="https://github.com/user-attachments/assets/f4299a8b-8531-4f77-8728-92b9a8f0614e" />

# Goal :  To use the stock check feature to scan the internal 192.168.0.X range for an admin interface on port 8080 and use a shellshock exploit to exfilrate the OS user.

# Ingrediants : Home, My account, view details. 
 
# Solving : 

- We Will firstly install the collobrator everywhere what it does is it will record all the request which goes to the external server without recorded in the internal response. 

<img width="1359" height="621" alt="image" src="https://github.com/user-attachments/assets/98fbd4c3-6ce3-4df9-8a77-5bb3160dcef9" />

- Then we view details and send that response to the repeater. We can notice that even without the user agent and Referer we got the positive response only. Hence both are vulnerable. 

<img width="1303" height="522" alt="image" src="https://github.com/user-attachments/assets/15497143-88e6-456b-bb70-6a5c0035bacb" />

<img width="1350" height="573" alt="image" src="https://github.com/user-attachments/assets/ad755719-6ecc-432d-9e18-71a4ded799be" />

- We will use the shell shock payload for the user agent of the burp colloborater server and find the username. 

<img width="894" height="535" alt="image" src="https://github.com/user-attachments/assets/08dfb3e8-4b5d-4347-ab32-881426936aea" />

- And in the referrer we will use the given ip. We will try the different ip by using the intruder.

<img width="1352" height="529" alt="image" src="https://github.com/user-attachments/assets/f4dfb79c-9c55-44c3-9f8f-fab6eca157a9" />

-

# ------------------------------------------------------------------------------

# 7. SSRF with whitelist-based input filter. 

<img width="754" height="160" alt="image" src="https://github.com/user-attachments/assets/f41ac334-dd71-401d-83a0-d0a567fbbbbb" />

# Goal :   To use the stock check feature to scan the internal 192.168.0.X range for an admin interface on port 8080 and delete carlos user. 

# Ingrediants : Home, My account, view details. 
 
# Solving : 

-  Lets check the stock and see the response. When we use only till .net it says illegal character error.

  <img width="1350" height="432" alt="image" src="https://github.com/user-attachments/assets/37d44b23-1932-4425-9ab0-30481f205263" />

- Lets try to access the local host url like in the previous labs. But it is not accessibile

<img width="1355" height="488" alt="image" src="https://github.com/user-attachments/assets/849a6273-a0ed-46fc-a06a-582aa4ffd7f3" />

- Let's try with the domanin and try to access the local host. And when we url encode the # we got a 200 response. 

<img width="1304" height="556" alt="image" src="https://github.com/user-attachments/assets/c26286b0-868d-4485-8c4a-318678939f79" />

- Hence by deleting the carlos user we solve the lab.

<img width="1331" height="547" alt="image" src="https://github.com/user-attachments/assets/97297bd7-bd9e-481f-a635-4f3d4f4833f2" />

<img width="1171" height="464" alt="image" src="https://github.com/user-attachments/assets/170367f6-0b42-4734-be22-ea98d0ee8aa9" />

<img width="1305" height="527" alt="image" src="https://github.com/user-attachments/assets/3d73862b-8fa1-40d0-895c-5da00384e9ca" />

# ------------------------------------------------------------------------------
