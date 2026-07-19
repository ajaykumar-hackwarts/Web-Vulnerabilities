# CORS : It stands for Cross Origin Resource sharing. It's browser security feature that decides wheather one websites is allowed to access data from another website. 

# 1. CORS vulnerability with basic origin reflection : 

<img width="743" height="194" alt="image" src="https://github.com/user-attachments/assets/db1c788a-1ac5-49b9-aa75-f0b3063c2d4f" />

# Goal : To craft some js that uses CORS to retrive administrator API key and upload to exploit server. 

# Ingrediants : exploit server, submit solution, home, my-account and view details button. 

<img width="1221" height="604" alt="image" src="https://github.com/user-attachments/assets/0a612ec9-c40a-48df-a2a2-0aa68d376874" />

# Solving : 

- Let's login

<img width="1246" height="523" alt="image" src="https://github.com/user-attachments/assets/981a7776-de0d-4b3e-a7b5-3743497a8e4f" />

- Let's see the request and response of the get request and will add a random website in the origin and see if the application accepts it.

<img width="1002" height="364" alt="image" src="https://github.com/user-attachments/assets/a02da2e5-6eca-4894-8b0f-b99743357187" />

- Hence we can see application allows orbitary origin.


















# ------------------------------------------------------------------------------
