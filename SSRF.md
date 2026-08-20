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


# 2. 
