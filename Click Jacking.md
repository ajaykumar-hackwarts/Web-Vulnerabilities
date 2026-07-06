<img width="853" height="522" alt="image" src="https://github.com/user-attachments/assets/ce27663b-ec76-41d6-9843-8c035dac518c" /># Clickjacking : Attack where user is tricked to click into something different from what they think they are clicking. 

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

 

