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

- <img width="1172" height="384" alt="image" src="https://github.com/user-attachments/assets/0fa9e8e9-43a1-4404-97d1-6530ff0d1a13" />

### Hence by posting this to exploit server we solve this. 
<img width="1357" height="386" alt="image" src="https://github.com/user-attachments/assets/9e0bdf96-b1ec-4ba5-b0b2-5c598a2ea3e2" />



# -------------------------------------------------------------------------------------------------------------------------------------------------------------------------
