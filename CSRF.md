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

<img width="1016" height="566" alt="image" src="https://github.com/user-attachments/assets/34ee87cf-a9eb-448c-8fcb-27b951438adb" />

- No unpredictable request parameters. Like the csrf token.

- We will use CSRF poc generator in the burpsuite pro to solve the lab. Which generates the csrf script for us including the submit button so when user clicks it it automaticlly submits it.

<img width="716" height="637" alt="image" src="https://github.com/user-attachments/assets/0a6330f7-918c-4cfe-b354-e685142deab3" />
 
- Hence let's change the email and copy the payload and upload it to expoit server.

<img width="1076" height="468" alt="image" src="https://github.com/user-attachments/assets/1f7fe853-c6ef-4b72-8fad-3bd6b7ca7842" />

<img width="1169" height="382" alt="image" src="https://github.com/user-attachments/assets/e47710bd-01f3-46de-92ed-26f30722ea23" />

- Hence by submitting that we solve the lab.

# ------------------------------------------------------------------------------

# 2. 
