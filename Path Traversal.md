<img width="1275" height="545" alt="image" src="https://github.com/user-attachments/assets/629a9e20-fbae-45cd-8321-b1c70a5b6067" /># Path Traversal : It's a vulnerability where the attacker tricks a webiste into reading files from the server that they should not be able to access. 

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


# 2. File path traversal, traversal sequences blocked with absolute path bypass. 

<img width="754" height="172" alt="image" src="https://github.com/user-attachments/assets/069362e4-36b3-452f-b2d5-8a5e38e5b4bb" />

## Goal :  Same as above.  

## Ingrediants :  Same as above. 

## Solving : 

- Like the last lab we will try to solve the lab ../

<img width="1168" height="460" alt="image" src="https://github.com/user-attachments/assets/90ff4048-c59f-4d2c-b13f-37d33d3bf8f7" />

- We can see it is failed. Now we will try that it is taking absolute path. 

<img width="1217" height="530" alt="image" src="https://github.com/user-attachments/assets/a035f158-428d-43d2-8222-4587a0350024" />

- It is taking the absolute path and we solved the lab.

<img width="1234" height="559" alt="image" src="https://github.com/user-attachments/assets/69ad49c2-ae0e-431a-baeb-20a8b7212557" />

# ------------------------------------------------------------------------------

# 3. File path traversal, traversal sequences stripped non-recursively. 

## Goal :  Same as above.  

## Ingrediants :  Same as above.

## Solving : 

- Like the last lab we will try to solve the lab ../ and absolute path.

<img width="1160" height="433" alt="image" src="https://github.com/user-attachments/assets/36afbcd1-d77f-4fad-9d17-d0e1e1c05842" />

<img width="1171" height="474" alt="image" src="https://github.com/user-attachments/assets/a687f927-16a4-491f-9cc0-549ad2e27116" />

- We can both is failed because the traversal sequence is stripped by the developer like whenever we see a sequence like ../ it will be filtered for that we will use the path like this ....//....//....// so after removing ../ we will still have another ../

<img width="1183" height="543" alt="image" src="https://github.com/user-attachments/assets/2d5380c8-cff5-40d9-bbf0-c66056fa43fa" />
 
- We can see it worked and we solved the lab.

<img width="1209" height="517" alt="image" src="https://github.com/user-attachments/assets/c8c4c77e-d3f8-4394-ac99-7b89b75189c6" />

# ------------------------------------------------------------------------------


