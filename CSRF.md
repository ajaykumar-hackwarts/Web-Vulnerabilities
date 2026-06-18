# CSRF(Cross Site request forgery) : Attacker tricks the victim's browser into sending unarthorized requests to trusted website where user is already authenticated. 

- Session cookie is saved by the browser.
- Attcker send a malicious csrf script link through WhatsApp, Telegram, SMS, or social media.
- When victim clicks the link and when the the page is loaded the script will be executed 
- Since the user is already authenticated, the browser automatically includes the session cookie.
- The target website recieves what appears to be legitimate requests from the autorised user and it may perform action if CSRF protection is not there.

# 1. CSRF vulnerability with no defenses  :

<img width="740" height="157" alt="image" src="https://github.com/user-attachments/assets/7a3d53bc-0796-47f9-a5c6-9609072f64cf" />

# Goal : To craft some html that uses csrf attack to change viewer's email address and upload to it exploit server. 

# Ingrediants : Exploit server, home, my account and view post button. 

<img width="878" height="509" alt="image" src="https://github.com/user-attachments/assets/5916939a-d3a5-4bfb-9d16-83b4198a36d1" />

# Solving : 

- Since we got a credentails we will login through that credentials.

<img width="1253" height="513" alt="image" src="https://github.com/user-attachments/assets/7b5f70c7-f6af-493f-8beb-1d4a76dd4525" />

- In order to perform csrf attack 3 things should be noted.

- Relevent action here that is email change functionality

<img width="861" height="507" alt="image" src="https://github.com/user-attachments/assets/5ab0f3a0-ec87-4a04-a1f5-200c7fb5cfef" />

- It should have cookie based session handling.

<img width="859" height="395" alt="image" src="https://github.com/user-attachments/assets/ebab70aa-477d-4d96-8a12-360633f85de9" />

- No unpredictable request parameters. Like the csrf token.

- We will use CSRF poc generator in the burpsuite pro to solve the lab. Which generates the csrf script for us including the submit button so when user clicks it it automaticlly submits it.

<img width="716" height="637" alt="image" src="https://github.com/user-attachments/assets/0a6330f7-918c-4cfe-b354-e685142deab3" />
 
- Hence let's change the email and copy the payload and upload it to expoit server.

<img width="1076" height="468" alt="image" src="https://github.com/user-attachments/assets/1f7fe853-c6ef-4b72-8fad-3bd6b7ca7842" />

<img width="1169" height="382" alt="image" src="https://github.com/user-attachments/assets/e47710bd-01f3-46de-92ed-26f30722ea23" />

- Hence by submitting that we solve the lab.

# ------------------------------------------------------------------------------

# 2. CSRF where token validation depends on request method

<img width="761" height="187" alt="image" src="https://github.com/user-attachments/assets/086baa4b-e944-4e10-8829-ae38d1de97d6" />

# Goal : Use exploit sever to host an html page that uses CSRF attack to change the email address.

# Ingrediants : Exploit server, home, my account and view post button. 

<img width="831" height="531" alt="image" src="https://github.com/user-attachments/assets/982bed6c-bb76-4e24-aa5c-f0fa163f8907" />

# Solving : 

- Since we got a credentails we will login through that credentials.

 <img width="1275" height="520" alt="image" src="https://github.com/user-attachments/assets/9a1d1538-7360-4e75-b28f-78d1a28ecae7" />

- As we know in order to perform csrf attack relevant action, cookie-based session handling and no unpredictable request parameters.

<img width="787" height="530" alt="image" src="https://github.com/user-attachments/assets/443fbbbe-35dd-40ff-a175-5a3374773dd7" />

- First 2 condition satisfied only the last condition is not satisfying to perform the csrf attack as it has the csrf token.

- To bypass the csrf token validation we will firstly try to change request method.

- When changing the request from post to get and followed the redirection we can see that it our changed email is there in the response.

<img width="861" height="409" alt="image" src="https://github.com/user-attachments/assets/44a84323-4c95-4eeb-87ab-4caadc0b7cc7" />

<img width="973" height="507" alt="image" src="https://github.com/user-attachments/assets/1cb9a5a5-1796-46a8-81a4-b15f11b793be" />

- We will try to delete the csrf token and update the email and see what will happen. 

<img width="914" height="458" alt="image" src="https://github.com/user-attachments/assets/140ab1fd-4e94-4cd9-8640-63cc85e0479e" />

<img width="1185" height="558" alt="image" src="https://github.com/user-attachments/assets/712322e7-0bba-40cd-8337-6e44e63be7e3" />

- But we can see only in the get method it doesn't required the csrf token but it needs in the POST method. 

<img width="1118" height="400" alt="image" src="https://github.com/user-attachments/assets/b1d6ab13-0da1-4dd5-9ea7-8e0572d5a53b" />

- We will use CSRF poc generator in the burpsuite pro to solve the lab. Which generates the csrf script for us including the submit button so when user clicks it. It automaticlly submits it.

<img width="1076" height="535" alt="image" src="https://github.com/user-attachments/assets/95f0cff5-bc1f-427b-85af-3a2cf6f27f1b" />

- Hence by submitting this we solve the lab. 

# ------------------------------------------------------------------------------


# 3. 
