# Access control vulnerabilities : It's a vulnerbility where application is fails to properly enforce the authorization rules, allowing user to access or perform action that they are not permitted to do it. 

# 1. Unprotected admin functionality. 

<img width="413" height="99" alt="image" src="https://github.com/user-attachments/assets/9cf0591b-7294-48fe-93db-525182f61be2" />

# Goal : To delete the carlos user. 

# Ingrediants : Home, My account, view details. 

<img width="1259" height="559" alt="image" src="https://github.com/user-attachments/assets/666fbd07-6aeb-4d5c-ad0d-ab8463cd17f8" />

# Solving : 

- Firstly we will try to brute force to enter the admin panel.

<img width="1209" height="561" alt="image" src="https://github.com/user-attachments/assets/fc3672a0-ff0a-4a68-83f0-0ea5720dc491" />

<img width="1184" height="415" alt="image" src="https://github.com/user-attachments/assets/e884ed2f-39bd-4262-9c14-62fddb667865" />

<img width="1119" height="422" alt="image" src="https://github.com/user-attachments/assets/5c86bd62-5811-42ab-9c5b-d1651e747f05" />

- Hence we can able to access the admin panel because of poor access control rules.  
 
<img width="1345" height="474" alt="image" src="https://github.com/user-attachments/assets/30e24861-00a4-4926-a22f-f7165129eb0e" />

- Hence by deleting the carlos user we solve the lab.

<img width="1228" height="488" alt="image" src="https://github.com/user-attachments/assets/59b0cb91-cbfa-41ba-80d5-1aa8ce5ed542" />

# ------------------------------------------------------------------------------
