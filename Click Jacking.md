# Clickjacking : Attack where user is tricked to click into something different from what they think they are clicking. 

# 1. Basic clickjacking with CSRF token protection : 

<img width="775" height="202" alt="image" src="https://github.com/user-attachments/assets/0059a556-5378-471b-ae1d-a450ece4fb59" />

# Goal : Craft html that fools the user into clicking into the delete account. 

# Ingrediants : My account, home, exploit server and view post button. 

<img width="947" height="547" alt="image" src="https://github.com/user-attachments/assets/1598661b-4adc-47b1-a1e2-cd41da1d1f6d" />

# Solving : 

- We will use the iframe to exploit this. Iframe(a web page displayed inside another web page) it stands for invisible frame. 

- When we login we can see it has the delete account button.

<img width="1253" height="526" alt="image" src="https://github.com/user-attachments/assets/2637f3cf-4f8a-4b0b-90a2-b7a0f448e9f4" />

- Hence we will try to build a overley and mislead the user to click the delete account button. To build the iframe we will use the exploit server and see the response.

<img width="1139" height="484" alt="image" src="https://github.com/user-attachments/assets/95b22129-4c88-493c-8bf5-048a17ce0e0a" />

- We builded the overlay. 

<img width="1039" height="403" alt="image" src="https://github.com/user-attachments/assets/052fc33d-1550-4c3b-a10c-4e4c4a7d8760" />

- Now we adjust the size of the frame/overlay.

<img width="1214" height="506" alt="image" src="https://github.com/user-attachments/assets/98f7fb50-bce4-4e0c-aaba-5201fa6140e9" />

- We successfully adjusted as a complete overlay of the page.

<img width="1077" height="520" alt="image" src="https://github.com/user-attachments/assets/38a1eb9c-1e12-452e-a2a2-77155f01693c" />

- Now we place the click me button over that overlay.

<img width="1025" height="363" alt="image" src="https://github.com/user-attachments/assets/076fdbbe-56fb-4a40-ab70-b9f301565f95" />

<img width="853" height="522" alt="image" src="https://github.com/user-attachments/assets/ae14ab56-60db-44de-a909-c5bcd001e266" />

- Now we will place on the Delete account.

<img width="1235" height="490" alt="image" src="https://github.com/user-attachments/assets/189da113-3b99-445a-92b5-4553f2735e91" />

- Hence we solved the lab by placing it on the delete account button. 

<img width="1243" height="469" alt="image" src="https://github.com/user-attachments/assets/3c6d3515-03f6-487e-a0d0-6209863309e0" />

# ------------------------------------------------------------------------------ 

# 2. Clickjacking with form input data prefilled from a URL parameter.

# Goal : Trick the user to click on the click me which in back end update the email. 

# Ingrediants : My account, home, exploit server and view post button. 

<img width="947" height="547" alt="image" src="https://github.com/user-attachments/assets/1598661b-4adc-47b1-a1e2-cd41da1d1f6d" />

# Solving : 

- Like the last lab we will login and build a overley using the iframe tab.

<img width="1133" height="560" alt="image" src="https://github.com/user-attachments/assets/d6ade022-58f0-49e3-b24c-d13b48941121" />

<img width="906" height="584" alt="image" src="https://github.com/user-attachments/assets/4ae01bc2-b131-4a34-b348-1af4fc45de54" />

- Now we will adjust teh size using the style.

<img width="1142" height="515" alt="image" src="https://github.com/user-attachments/assets/21dee915-2a3e-4289-aba5-9ef207b5111a" />

<img width="1235" height="610" alt="image" src="https://github.com/user-attachments/assets/222d7435-f674-4ec5-bcd5-b9677499f059" />

-  Hence we solved the lab by decreasing the opacity and deliver the script to the user. 

<img width="1153" height="581" alt="image" src="https://github.com/user-attachments/assets/b34d27ad-4e10-463a-b183-4bc4b4bc0fa3" />

# ------------------------------------------------------------------------------ 


# 3. Clickjacking with a frame buster script.

<img width="779" height="255" alt="image" src="https://github.com/user-attachments/assets/d80b86e9-fcc7-4562-87ac-b1b1edd23787" />

# Goal : Trick the user to click on the click me which in back end update the email. 

# Ingrediants : Same as above. 

# Solving : 

- Like the last lab we will try to build th iframe.

<img width="1026" height="519" alt="image" src="https://github.com/user-attachments/assets/4d904143-f447-4ca9-b1a0-46f27ffc7621" />

- And it says the page cannot be framed. 

<img width="576" height="353" alt="image" src="https://github.com/user-attachments/assets/fe692feb-2667-4a4f-9a56-95665dd4e29c" />

- Let's try bypass this by using sandbox.

<img width="1331" height="473" alt="image" src="https://github.com/user-attachments/assets/91a0f66a-d908-4824-b94b-e94be87ddf41" />

- We have bypassed it as we can see the iframe. 

<img width="910" height="461" alt="image" src="https://github.com/user-attachments/assets/26f393a6-88e5-4062-85e8-06ddd39ab7f1" />

- Now we will style and place the click me button on the top of update email. 

<img width="1155" height="418" alt="image" src="https://github.com/user-attachments/assets/b65a59cc-3a72-421d-ab7c-f001810a4a37" />

<img width="863" height="540" alt="image" src="https://github.com/user-attachments/assets/c1765e01-72a3-409c-a290-67f16252ecdd" />

<img width="1276" height="470" alt="image" src="https://github.com/user-attachments/assets/c5695eb5-3178-4e39-be9a-d78aebd08ebd" />

- Hence by pasting this we solve the lab.

<img width="1245" height="454" alt="image" src="https://github.com/user-attachments/assets/fb9b0b54-3b1d-4aa5-a5cd-4f882d78cd49" />

# ------------------------------------------------------------------------------ 


# 4. Exploiting clickjacking vulnerability to trigger DOM-based XSS. 

<img width="748" height="88" alt="image" src="https://github.com/user-attachments/assets/12acecc0-daca-483d-bd8b-c20505f41ea0" />

# Goal : Trick the user to click on the click me which calls the print(). 

# Ingrediants :  Submit feedback, home, exploit server and view post button. 

<img width="1007" height="486" alt="image" src="https://github.com/user-attachments/assets/96801112-bcb3-4b1b-8073-f37d9a95b237" />

# Solving : 

- Let's firstly try to submit the feedback with random values.

<img width="878" height="569" alt="image" src="https://github.com/user-attachments/assets/25689b70-2a22-404a-a5bc-a0385040f2b8" />

<img width="847" height="562" alt="image" src="https://github.com/user-attachments/assets/a4ab0f16-ad02-4dea-bfe2-2eaf685c4416" />

- Now we will try to submit DOM based Xss script and check it is vulnerable to xss or not. 

<img width="862" height="568" alt="image" src="https://github.com/user-attachments/assets/c3f07e57-887b-4d92-88b8-78e3e9030a64" />

- And it poppud up hence it is vulnerable to xss. 

<img width="1071" height="539" alt="image" src="https://github.com/user-attachments/assets/4be508f1-ef9c-4397-ac55-cfaaca55acec" />

- Now we will try to check if it is prepopulating the value when we giving in the query paramter of the url and it is possible to prepoulate. 

<img width="1215" height="633" alt="image" src="https://github.com/user-attachments/assets/30c192ba-00cd-4e9a-8c43-1cbbd81c45ae" />

- Now we have to build the iframe and place the click me button on the submit feedback.

<img width="1053" height="517" alt="image" src="https://github.com/user-attachments/assets/f0d8e4e5-602d-46c5-851a-6d02b884979a" />

- Hence by submitting the script to exploit server we solve the lab.

<img width="778" height="578" alt="image" src="https://github.com/user-attachments/assets/2a3a6753-061e-4653-b3e4-4e5e0be65bef" />

# ------------------------------------------------------------------------------ 


# 5.  
