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


# 3. CSRF where token validation depends on token being present. 

<img width="781" height="151" alt="image" src="https://github.com/user-attachments/assets/c32ff0e7-009e-4ba1-9be1-aba34d207daf" />

# Goal :  Use exploit sever to host an html page that uses CSRF attack to change the email address.

# Ingrediants : Same as above. 

# Solving : 

- Let's check it is satisfying all the conditions or not.

<img width="1120" height="545" alt="image" src="https://github.com/user-attachments/assets/fbf9d102-84b2-4b2e-83a4-e2a2fa2197a1" />

<img width="1053" height="474" alt="image" src="https://github.com/user-attachments/assets/8cdea0f0-d06b-4827-9f9c-e14bc44139de" />

- Unlike the last lab instead of changing the request method and checking the csrf token is required or not we will try to remove the csrf token in the POST metod itself. And we can see it is worked. 

<img width="1107" height="528" alt="image" src="https://github.com/user-attachments/assets/71660f37-2777-4f1b-b4ad-2aeff069e4e7" />

- Like the last lab we will use the CSRF poc generator for exploit. Hence we can see we solved the lab by uploading the script.   

<img width="1233" height="444" alt="image" src="https://github.com/user-attachments/assets/2724ef0b-0370-422e-b61e-93185121d9ed" />

<img width="1223" height="408" alt="image" src="https://github.com/user-attachments/assets/61c48b65-b9d1-45dd-ac2e-4050f30ce9ed" />

# ------------------------------------------------------------------------------

# 4. CSRF where token is not tied to user session

<img width="820" height="291" alt="image" src="https://github.com/user-attachments/assets/9f54fb74-c933-4633-b470-c60ae489b9d3" />

# Goal :  Use exploit sever to host an html page that uses CSRF attack to change the email address.

# Ingrediants : Same as above. 

# Solving : 

- Let's check it is satisfying all the conditions or not.

<img width="1213" height="504" alt="image" src="https://github.com/user-attachments/assets/351736ba-cca9-4152-8678-50cd7b88a995" />

<img width="1049" height="521" alt="image" src="https://github.com/user-attachments/assets/e648f30e-83cd-42e3-b922-9e4069db0ee6" />

- Lets check the csrf token is needed or not then we will change it to request method.

<img width="1068" height="453" alt="image" src="https://github.com/user-attachments/assets/6e12ad98-6ede-4d72-b430-7f4ab28ed861" />

<img width="1144" height="425" alt="image" src="https://github.com/user-attachments/assets/ce1310e9-acfc-4e12-9d49-f0b4412a88ae" />

- Hence both are not working. Let's check if it is actually need a valid csrf token by added extra string there. We can see it does need a valid token. 

<img width="996" height="476" alt="image" src="https://github.com/user-attachments/assets/5c85c459-9aa4-4a9c-a3fe-0102f56caadf" />

- Let's check that if the csrf token is tied to the session id or not by taking the valid crsf token from attacker carlos:montoya account and use here.  

<img width="1078" height="480" alt="image" src="https://github.com/user-attachments/assets/03d4ebe9-94ac-4fca-8aeb-8fd8910ed16c" />

<img width="1107" height="559" alt="image" src="https://github.com/user-attachments/assets/7908f410-fd51-44be-bfd5-ccd4a6bb8ff6" />

- We can see it worked hence csrf token is not tied to the session id. 

<img width="1052" height="658" alt="image" src="https://github.com/user-attachments/assets/a2e7be5f-964d-4134-b95e-e8a60901b6c7" />

- Let's generate the script using the Poc generator and submit in the exploit server. 

<img width="937" height="448" alt="image" src="https://github.com/user-attachments/assets/01ed776c-d2a7-4f18-8f0a-473d939bea96" />

<img width="1108" height="554" alt="image" src="https://github.com/user-attachments/assets/189c0f01-9784-4135-886d-7c1987e5b6f4" />

- Hence we solved the lab by uploading that. 

<img width="1143" height="425" alt="image" src="https://github.com/user-attachments/assets/5c39c1d1-57de-415f-b712-c2fe633be9dd" />

# ------------------------------------------------------------------------------

# 5. 
