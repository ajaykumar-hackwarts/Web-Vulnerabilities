<img width="989" height="203" alt="image" src="https://github.com/user-attachments/assets/67767b07-253a-4924-8586-cb3bce01e003" /><img width="1264" height="535" alt="image" src="https://github.com/user-attachments/assets/d2d08288-9d1c-4778-9a91-f1a6b6bf55a9" />

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

Same as above

 ## Solving :

- Let's click on the viewpost and we can see it has a redirection page like return page button back to blog that will be our vulnerable parameter
- We will view the source code
<img width="1135" height="192" alt="image" src="https://github.com/user-attachments/assets/bfa3d837-3d26-40fd-bf92-c4146e8928ce" />

- We can see it redirecting by the return url Hence we can exploit that.
- By placing url="" exploit server url after victim url seperating by # or &. It wil look like the following.

<img width="1356" height="326" alt="image" src="https://github.com/user-attachments/assets/1374a18a-b096-4622-a7f4-e35ac473123f" />

### Hence by posting this to exploit server we solve this. 


# -----------------------------------------------------------------------------------------------


5. DOM-based cookie manipulation

<img width="770" height="108" alt="image" src="https://github.com/user-attachments/assets/9bed505c-a34b-43af-87e4-88b02e0e432a" />

**Goal** :  Inject a cookie that will cause XSS on a different page and call print(). 

### Ingredients :  
We have the view details button. 

<img width="1332" height="450" alt="image" src="https://github.com/user-attachments/assets/53862ff2-0f69-42da-bc77-d1b2cc9db762" />

After visiting the page and returning to list we can see it has last viewed product. 

<img width="1283" height="501" alt="image" src="https://github.com/user-attachments/assets/d751e28f-b406-4f53-924e-a7c75fc6c4d8" />

<img width="1264" height="535" alt="image" src="https://github.com/user-attachments/assets/5e89ff31-b807-4cfe-8bc1-423096b9d3a4" />

 ## Solving :

 - That last viewed product is our vulnerable parameter.

 - When we intercept the response and we can see in the value after the id is appendable we can able to modify and still it gives the 200 response.
 - Also in the response side we can see cookie is set to lastViewedProduct and samesite is set to none so it exploitable to cross site. 

<img width="1365" height="462" alt="image" src="https://github.com/user-attachments/assets/38af96d0-aa21-4f2d-825c-59c2d0b5a1fe" />

- When we see the click the lastviewedproduct we can it is returning to the same url in the <a 

<img width="1360" height="406" alt="image" src="https://github.com/user-attachments/assets/5d9a7614-c939-48c0-9340-c73c4262b00f" />

- We have to break the tag like close the tag and open a new script and put a print payload there.

<img width="989" height="203" alt="image" src="https://github.com/user-attachments/assets/c2a1bbb0-9a3f-42d5-80f2-1f9fd35ab9bb" />

<img width="991" height="315" alt="image" src="https://github.com/user-attachments/assets/255f5ef4-18f9-4dcd-a458-b861f0e2caa8" />

- These payload will only print but we have to put the XSS payload so  we put the complete payload as follows. 

<iframe src="&'><script>print()</script>" onload="if(!window.x)this.src='https://YOUR-LAB-ID.web-security-academy.net';window.x=1;">

- onload ---> after loading the iframe 
- if(!window.x) ----> if windows doesn't have the x element then source will set to this url which is home page so the before payload print is set and return to home page immediately.
- window.x=1 ---> then x is set to 1 so it will run only one time avoiding the loop.


### Hence by posting this to exploit server we solve this. 


# -----------------------------------------------------------------------------------------------


6. Exploiting DOM clobbering to enable XSS

<img width="783" height="121" alt="image" src="https://github.com/user-attachments/assets/41a93177-8fe7-4fcc-8476-5751a5e0b3f4" />


**Goal** :  Injecting a html that clobbers the variable and use XSS to call alert(). 


 
