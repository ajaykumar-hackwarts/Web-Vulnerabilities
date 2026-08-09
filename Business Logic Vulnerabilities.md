# Business Logic Vulnerabilities : It is a vulnerability where application works correctly as programmed but the business rules are flawed like the user manipulate and use the application as they shouldn't be able to.

## Example : Like app has a product for price 1000 and discount coupon is 10% and app accidentaly allows to apply the coupon for multiple times 

# 1. Excessive trust in client-side controls.

<img width="741" height="169" alt="image" src="https://github.com/user-attachments/assets/015d646d-a305-4750-86db-c82aa51eccb8" />

# Goal : To Buy a "Lightweight l33t leather jacket".

# Ingrediants : Home, My account, view details. 

<img width="1293" height="541" alt="image" src="https://github.com/user-attachments/assets/1e4755fc-2bd5-430e-8446-99452c643bae" />

# Solving : 

- Let's login and add the jacket to the cart.

<img width="915" height="554" alt="image" src="https://github.com/user-attachments/assets/d88f0040-69b7-4a9d-a1cb-56e7db52b875" />

<img width="1049" height="540" alt="image" src="https://github.com/user-attachments/assets/c9840e77-4897-43db-911d-c9bae72d7066" />

 <img width="1063" height="478" alt="image" src="https://github.com/user-attachments/assets/245a6db2-ffdb-42d9-91e9-956c6a13cac5" />

 - We can see that in the request it is sending the price in the request too. And when we sending the request using the repeater it is adding the item again 

<img width="877" height="561" alt="image" src="https://github.com/user-attachments/assets/4abe666c-04cb-458d-8a39-5f81873d8488" />

- Hence let's try that can we able to change the amount or not. We can able to change the price of the jacket

<img width="1011" height="500" alt="image" src="https://github.com/user-attachments/assets/50902097-dd7d-41de-a897-31582ff9381e" />

<img width="1037" height="599" alt="image" src="https://github.com/user-attachments/assets/7e757431-49ce-49fa-8425-bfaaa67b9d4e" />

- Hence by placing the order we solve the lab.

<img width="1036" height="470" alt="image" src="https://github.com/user-attachments/assets/43747825-e3b0-4767-8702-30d89f17c0f8" />


# ------------------------------------------------------------------------------

