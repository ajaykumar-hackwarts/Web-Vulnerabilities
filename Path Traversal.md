# Path Traversal : It's a vulnerability where the attacker tricks a webiste into reading files from the server that they should not be able to access. 

# 1.  File path traversal, simple case

<img width="682" height="100" alt="image" src="https://github.com/user-attachments/assets/336722d6-746b-487e-8fe5-8ad13e8f6b99" />

## Goal :  To retrieve the contents of the /etc/passwd file. 

## Ingrediants :  Home and view details button. 

<img width="1287" height="564" alt="image" src="https://github.com/user-attachments/assets/e9a01ada-64f9-4824-a925-8738ac80ae9f" />

## Solving : 

- First we will try to see the response of the images.

<img width="1349" height="470" alt="image" src="https://github.com/user-attachments/assets/ed2e5702-79c9-44f2-9dec-e4f823a21451" />

- We can see it is getting the file from the /image directory. First we will try if it is absolute paths /

<img width="1248" height="481" alt="image" src="https://github.com/user-attachments/assets/cd6f050e-396c-4f9a-9afc-6c4e6df8c5fc" />

- Since it is failed we will try to go to the root directory and check this path etc/passwd for that we will use ../ what it does is it will move on to the previous directory

- Example /var/www/image is the path means when we give ../etc/passwd means it will go to /var/www/etc/passwd and move on to further.

<img width="1351" height="605" alt="image" src="https://github.com/user-attachments/assets/9647a9d4-2462-4206-8ee8-8cc19e03824c" />

- We can see it worked and we gone to the root directory and solved the lab.

<img width="1275" height="545" alt="image" src="https://github.com/user-attachments/assets/da1a4b55-9748-4c98-854f-b0fb1cfce521" />

# ------------------------------------------------------------------------------
