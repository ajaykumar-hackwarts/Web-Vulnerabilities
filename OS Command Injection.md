# OS Command Injection : It's an attack where attacker executes an arbitory operating system commands on the server running on the application. 

# 1. OS command injection, simple case

# Goal :  To execute the whoami command to determine the name of the current user. 

# Ingrediants :  Home and view details button. 

<img width="1294" height="594" alt="image" src="https://github.com/user-attachments/assets/389d7fdf-b1a0-41ed-8f83-e3744b2a2c25" />

# Solving : 

- Let's check the stocks and intercept the request in the burp.

<img width="1054" height="505" alt="image" src="https://github.com/user-attachments/assets/9849644a-3799-445b-8915-d197a635f717" />
 
- Now we will try to execute the whoami command and find the user. We solve the lab. 

<img width="1095" height="510" alt="image" src="https://github.com/user-attachments/assets/1426123f-0bf8-42c9-aee7-1a83b1cffeef" />

 <img width="1292" height="538" alt="image" src="https://github.com/user-attachments/assets/442158f8-311b-44f5-a6dd-aa5d3f906a67" />

- Even thoough we solve the lab we will the find the content of the script this is running.

<img width="1098" height="473" alt="image" src="https://github.com/user-attachments/assets/cf5aa24a-da96-429d-8c7d-a888067654be" />

- We will try to read the content of this script.

<img width="1220" height="427" alt="image" src="https://github.com/user-attachments/assets/580a13f0-4e04-40b9-b47c-b7820febeda3" />

<img width="1132" height="543" alt="image" src="https://github.com/user-attachments/assets/34566bf8-c9db-4856-bd49-e0bf33e7a211" />

- Hence we can see it is using the bash script which is using the eval that it used to execute the os commands they are executing commands directly from the user input without any validation. 

# ------------------------------------------------------------------------------


# 2. 
