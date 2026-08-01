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

