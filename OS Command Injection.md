<img width="1346" height="600" alt="image" src="https://github.com/user-attachments/assets/7018ab2f-3053-4f30-8381-0f199728a5fb" /><img width="1346" height="600" alt="image" src="https://github.com/user-attachments/assets/fcd2cb1d-2a05-4412-b2cb-41978e6ed357" /># OS Command Injection : It's an attack where attacker executes an arbitory operating system commands on the server running on the application. 

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


# 2. Blind OS command injection with time delays. 

<img width="765" height="200" alt="image" src="https://github.com/user-attachments/assets/6f5187d9-8e2d-4801-a092-107ff953ab6a" />

# Goal :  To exploit blind OS command injection to cause 10 second delay. 

# Ingrediants :  Home, Submit feedback and view details button. 

<img width="1320" height="603" alt="image" src="https://github.com/user-attachments/assets/bcbfa57b-0de1-4714-8b91-32081b92a5ae" />

# Solving : 

- We will submit a feedback and check the response.

<img width="1000" height="574" alt="image" src="https://github.com/user-attachments/assets/3a9d6215-ffba-436b-ba58-d9543452b8b4" />

<img width="1024" height="428" alt="image" src="https://github.com/user-attachments/assets/74178ac7-d56a-4a93-b4aa-61f56e34d648" />

- And we will check which field is vulnerable to os command injection. We can see name feild is not vulnerable. 

<img width="1362" height="612" alt="image" src="https://github.com/user-attachments/assets/14992689-fd05-4652-b361-52d519302c91" />

- We can it has the 10 second time delay hence email feild is vulnerable. Hence we solved the lab.  

<img width="1336" height="643" alt="image" src="https://github.com/user-attachments/assets/69b0aa85-3ea9-4b4d-a963-6ffc7c05f2ac" />

<img width="1341" height="528" alt="image" src="https://github.com/user-attachments/assets/3ab04429-f2c0-4ab3-9548-b737a00a16af" />

# ------------------------------------------------------------------------------


# 3. Blind OS command injection with output redirection. 

<img width="813" height="340" alt="image" src="https://github.com/user-attachments/assets/c8236d49-9567-4f69-89a7-c485abe52fd1" />

# Goal :  To execute the whoami command and retrive the output. 

# Ingrediants :  Same as above. 

<img width="1282" height="584" alt="image" src="https://github.com/user-attachments/assets/52075a0d-57fd-4db7-a50d-1db49681808f" />

# Solving :  

- Like the last lab we will check the app is vulnerable to blind OS command injection or not. And it is vuklnerable to blind OS command injection. 

<img width="1339" height="591" alt="image" src="https://github.com/user-attachments/assets/a2ae83cc-61a7-468f-b4dd-9c8d41d5c00a" />

- We will go back to the home and see anything is helpful for us in the response.

<img width="1346" height="600" alt="image" src="https://github.com/user-attachments/assets/ccf4d55e-5662-4672-ac64-e8b7ba8c4011" />

- We can get the username by simply by using the whoami command like the previous labs. 

<img width="1300" height="495" alt="image" src="https://github.com/user-attachments/assets/2eec3284-36f9-47e7-92ca-e2492e916e2b" />

- We can see the images are stored in /var/www/images/. 

<img width="1063" height="543" alt="image" src="https://github.com/user-attachments/assets/4dec8ecc-d862-4349-a8be-26d3b3bfa367" />

- So we will try to implement the whoami command by creating a new file in this path.

<img width="1119" height="467" alt="image" src="https://github.com/user-attachments/assets/8128acf8-0644-4dc5-bc21-e0e6d94c4220" />

- And we can see it has teh username in the path and we solved the lab successfully.

<img width="1034" height="374" alt="image" src="https://github.com/user-attachments/assets/5d6d8e0e-2578-4b32-90a0-09e346ae34e5" />

<img width="1290" height="569" alt="image" src="https://github.com/user-attachments/assets/255589e6-209b-4a09-9eff-496dd3f6aeaf" />

# ------------------------------------------------------------------------------


# 4. Blind OS command injection with out-of-band interaction. 

<img width="802" height="246" alt="image" src="https://github.com/user-attachments/assets/a0a71739-2f58-4b51-a47a-d70969041e5a" />

# Goal : To exploit blind OS command injection to issue DNS lookup. 

# Ingrediants :  Same as above. 


