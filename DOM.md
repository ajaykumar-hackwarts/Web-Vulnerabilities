

**Definition** : DOM(Document Object Model) is a Tree-like structure that browser creates from the html. So that it can display and edit the page using javascript. 

# 1. DOM XSS using web messages
 <img width="778" height="113" alt="image" src="https://github.com/user-attachments/assets/48d7cc5b-af61-492f-8258-c50a7e9d3796" />

- **Goal** : Send a message to the target site in that message we write a code to call print.

### Ingredients : 

 <img width="1240" height="618" alt="image" src="https://github.com/user-attachments/assets/38886b35-ddaf-47b6-b7bd-2b6e64343328" />

 - **Buttons** : We got exploit server, home and view details button.

- Lets check the exploit server.

<img width="1225" height="371" alt="image" src="https://github.com/user-attachments/assets/edd4bc5b-86ce-457b-bde6-222ea658491a" />

Here we are going to write the code which will call the print() from the target site. 

## Solving : 

- We will use iframe(invisible frame which is used to load another webpage inside our page). Like this <iframe src="">
- Inside the iframe we have to post a message that will call print() hence we will use this onload="this.contentWindow.postMessage
- ('<img  
- src=1 onerror=print()>','*'). 
- onload - after loading the webpage inside the iframe
- this - current element in this case iframe website.
- contentWindow - Reference to window object inside the iframe.
- postMessage - send a message to another window.
- <img 
- src=1 onerror=print()> - This is the page load we are going to send it's a image fails to load becasue src=1 hence it trigers the onerror and print.
- '*' - Sends the message to the website regardless of the origin(http://abc.com:443 - protocol+Domain+port = origin)

<img width="1172" height="384" alt="image" src="https://github.com/user-attachments/assets/0fa9e8e9-43a1-4404-97d1-6530ff0d1a13" />

### Hence by posting this to exploit server we solve this. 
<img width="1357" height="386" alt="image" src="https://github.com/user-attachments/assets/9e0bdf96-b1ec-4ba5-b0b2-5c598a2ea3e2" />



# -----------------------------------------------------------------------------------------------


# 2. DOM XSS using web messages and a JavaScript URL 

<img width="762" height="122" alt="image" src="https://github.com/user-attachments/assets/2ca61e04-648a-4b61-9976-a14b7c3721b0" />

- **Goal** : Send a message to the target site in that message we write a code to call print.

### Ingredients : 

<img width="1084" height="604" alt="image" src="https://github.com/user-attachments/assets/b9e36d71-c379-4d43-8d85-912fc8f2b504" />

 - **Buttons** : We got exploit server, home and view post button.

## Solving :

- Everything is same as the previous lab except the pay load. Here we use javascript:print()//http: inside the post message like
- <iframe src="" onload="this.contentWindow.postMessage('javascript:print()//http:','*')">
- Becasue here we want to exploit DOM XSS using the JS Url. Hence we using this payload javascript:print()//http:
- javascript: - Tells the broswer run the following as the JS code.
- print() - Print
- // - ignore the rest and http: -> protocol

<img width="1236" height="424" alt="image" src="https://github.com/user-attachments/assets/07fc909f-87c6-4e3e-a71f-fc575a6c9492" />
### Hence by posting this to exploit server we solve this. 

# -----------------------------------------------------------------------------------------------


# 3. DOM XSS using web messages and JSON.parse

<img width="771" height="122" alt="image" src="https://github.com/user-attachments/assets/81ff46b7-796c-4589-b70b-dc8d1ea9fb7e" />

 **Goal** : Send a message to the target site in that message we write a code to call print.

 ### Ingredients :  Same as above. 

 ## Solving :

 - The difference in the pay load is \"type\":\"load-channel\",\"url\":\"javascript:print()\"
 - Since Json uses the " for the strings and keys since our string already contains the " so system will show it as syntax error. Hence to neglect the error we using the escaping character \ before the "
 - So normaly it would look like type : load-channel, url : javascipt: print()
 - type : load-channel ---> Tells the reciver victim page what function to run.
 - url : javascipt: print() ---> Print

<img width="1191" height="398" alt="image" src="https://github.com/user-attachments/assets/94313d94-a265-43d1-af17-9013d8715e56" />

### Hence by posting this to exploit server we solve this. 


# -----------------------------------------------------------------------------------------------



# 4. DOM-based open redirection

<img width="760" height="76" alt="image" src="https://github.com/user-attachments/assets/d82353ab-0667-4bc2-beb9-334966dfb84c" />

**Goal** : Redirect the victim to the exploit server

### Ingredients :  


 ## Solving :

- Let's click on the viewpost and we can see it has a redirection page like return page button back to blog that will be our vulnerable parameter
- We will view the source code
<img width="1135" height="192" alt="image" src="https://github.com/user-attachments/assets/bfa3d837-3d26-40fd-bf92-c4146e8928ce" />

- We can see it redirecting by the return url Hence we can exploit that.
- By placing url="" exploit server url after victim url seperating by # or &. It wil look like the following.

<img width="1356" height="326" alt="image" src="https://github.com/user-attachments/assets/1374a18a-b096-4622-a7f4-e35ac473123f" />

### Hence by posting this to exploit server we solve this. 


# -----------------------------------------------------------------------------------------------

