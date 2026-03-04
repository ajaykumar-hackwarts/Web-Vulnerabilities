<img width="1258" height="434" alt="image" src="https://github.com/user-attachments/assets/5996b4cc-c888-48f7-96cd-9955e1923e0f" /><img width="989" height="203" alt="image" src="https://github.com/user-attachments/assets/67767b07-253a-4924-8586-cb3bce01e003" /><img width="1264" height="535" alt="image" src="https://github.com/user-attachments/assets/d2d08288-9d1c-4778-9a91-f1a6b6bf55a9" />

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

### Ingredients :  
We have the view post button. 

<img width="888" height="483" alt="image" src="https://github.com/user-attachments/assets/013141fe-ec3b-4849-baa8-26f97bebf1c0" />

- In comment section when we see the previous comments we can see it has an avatar and it says HTML is allowed. 

<img width="812" height="459" alt="image" src="https://github.com/user-attachments/assets/9045984b-c6b1-4f95-8335-ca753b770e1e" />

- The loadCommentsWithDomClobbering.js looks good. Hence we look into that and we can see it has this.  

<img width="1364" height="516" alt="image" src="https://github.com/user-attachments/assets/d64d9c18-71d8-41e7-87b6-3798265d659b" />

let defaultAvatar = window.defaultAvatar || {avatar: '/resources/images/avatarDefault.svg'}

- They setting the defaultAvatar to window.defaultAvatar or it will use the pre defined value '/resources/images/avatarDefault.svg'. It will check in window.defaultAvatar is any avatar available. There were we will inject our malicious payload to clobber.
- <a id=defaultAvatar><a id=defaultAvatar name=avatar href="cid:&quot;onerror=alert(1)//">
- To clobber a value we should set an ID/variable with the same name after that inside the href value we will give this as
- cid: --> Content ID which is used in email to attach the image/files. Since it not go out on a web it is used inside the html the DOMpurify takes it as non malicious and it allows it.
- &quot; ---> It is encoded format of " hence when run time it will be decoded as href="cid:"onerror=alert(1)//" Making the code execute and the alert will be triggered. 

- This will be our first malicious comment. 

<img width="775" height="586" alt="image" src="https://github.com/user-attachments/assets/aa0a876a-8e44-4fc9-b9d5-1f47edd3840a" />

- Out next comment would be normal random comment this is to set window.defaultAvatar to our malicious payload and it don't use /resources/images/avatarDefault.svg

<img width="768" height="566" alt="image" src="https://github.com/user-attachments/assets/7c15b9ae-6fb6-4e56-b9f4-13c06b8c8790" />

The window.defaultAvatar is set our payload. 

<img width="692" height="312" alt="image" src="https://github.com/user-attachments/assets/fb25c5ad-a352-4261-8e82-f07b3a58cef6" />

The last comment is to load the avatar again to call the alert()

<img width="883" height="569" alt="image" src="https://github.com/user-attachments/assets/8b0aaf69-5c6e-4674-94cf-ab3194d84201" />



### Hence by doing this to exploit server we solve this. 

<img width="1328" height="377" alt="image" src="https://github.com/user-attachments/assets/5121eed0-2450-4aa0-afe4-bce34f376b12" />


# -----------------------------------------------------------------------------------------------



# 7. Clobbering DOM attributes to bypass HTML filters

<img width="797" height="139" alt="image" src="https://github.com/user-attachments/assets/58cd4c9e-9acf-413a-9830-f6ce6e5224e9" />

**Goal** : Construct a vector to bypass html filters and using DOM clobbering inject a vector that calls print(). 

### Ingredients :  

<img width="957" height="487" alt="image" src="https://github.com/user-attachments/assets/62090b1b-7386-48f8-b218-494c959cb0b1" />

Since the app is using the Html filtering we can't use the html tags here. 

<img width="850" height="579" alt="image" src="https://github.com/user-attachments/assets/cdb9f088-8200-4144-868c-b3c5f6a9472e" />

- When we look into the source code we can see it is using two js file htmlJanitor.js and loadCommentsWithJanitor.js 

<img width="699" height="193" alt="image" src="https://github.com/user-attachments/assets/d9787390-fb10-465d-bd3e-d102b7ea5712" />

- In the htmlJanitor.js inside the santize attributes it is cleaning the attribues like int, src etc...

<img width="481" height="200" alt="image" src="https://github.com/user-attachments/assets/da70dcf7-21e2-45c2-8110-8a02df3e3093" />

- Hence we create a payload in a form and post in the comment as html is not allowed. Like the following. 

<img width="770" height="555" alt="image" src="https://github.com/user-attachments/assets/3e02eb85-e42f-45a1-a6a8-d71dcbc81a8c" />

- <form id=x tabindex=0 onfocus=print()><input id=attributes>
- id=x ---> we creating a id named x
- tabindex=0 ---> We make it focusable first as the index is 0 first it will be focused.
- onfocus=print() --> when the tabindex is focused it will print().
- <input id=attributes> --> It clobbers the real attribute and replace our payload and no neglect the print().

It will result like this. 
<img width="870" height="346" alt="image" src="https://github.com/user-attachments/assets/2303bc35-f73a-4ffe-9b55-22241a3bca04" />

- After that we will post the following in the exploit server. 
<iframe src=https://YOUR-LAB-ID.web-security-academy.net/post?postId=3 onload="setTimeout(()=>this.src=this.src+'#x',500)">

- <iframe src=https://YOUR-LAB-ID.web-security-academy.net/post?postId=3 ---> First it will load the normal url.
-  onload="setTimeout(()=>this.src=this.src+'#x',500) --> after loading the normal url it will wait for 500ms then append the src to #x making the print() to execute.

<img width="1240" height="440" alt="image" src="https://github.com/user-attachments/assets/0cbcc106-6a2e-4619-aadf-9571657013a4" />


### Hence by posting this to exploit server we solve this.

# -----------------------------------------------------------------------------------------------
