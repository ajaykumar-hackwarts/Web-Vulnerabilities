<img width="992" height="349" alt="image" src="https://github.com/user-attachments/assets/491f1e6e-a942-4fe1-a881-a131f64fbbf1" /># CSRF(Cross Site request forgery) : Attacker tricks the victim's browser into sending unarthorized requests to trusted website where user is already authenticated. 

- Session cookie is saved by the browser.
- Attacker send a malicious csrf script link through WhatsApp, Telegram, SMS, or social media.
- When victim clicks the link and when the the page is loaded the script will be executed 
- Since the user is already authenticated, the browser automatically includes the session cookie.
- The target website recieves what appears to be legitimate requests from the authorised user and it may perform action if CSRF protection is not there.

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

# 5. CSRF where token is tied to non-session cookie. 

<img width="811" height="308" alt="image" src="https://github.com/user-attachments/assets/2b931e65-7d95-485d-a51c-9ac6ea916b53" />

# Goal :  Use exploit sever to host an html page that uses CSRF attack to change the email address.

# Ingrediants : Same as above and extra it has the search tab. 

<img width="1001" height="493" alt="image" src="https://github.com/user-attachments/assets/11b8bf7b-cd30-49d0-95e1-8a3b76ea4524" />

# Solving : 

- Let's try all the possibilities that we tried in the previous lab.

<img width="1330" height="462" alt="image" src="https://github.com/user-attachments/assets/a76edb4e-5bec-4a60-983f-992ede56aba9" />

<img width="1082" height="496" alt="image" src="https://github.com/user-attachments/assets/13ac93d3-e19a-4da0-9e1d-53ac6911afd7" />

<img width="998" height="485" alt="image" src="https://github.com/user-attachments/assets/24c3291c-c1a1-45bc-a8cb-4e3031ddcd8a" />

- We can see it has one add on cookie with session cookie which is csrf key cookie. We will try to add csrf token and crsfkey cookie from attacker account.

<img width="1022" height="509" alt="image" src="https://github.com/user-attachments/assets/2503faac-8d1a-4c5c-95c2-0b05d1d9d286" />

<img width="1285" height="396" alt="image" src="https://github.com/user-attachments/assets/c288ca70-42aa-4d8c-a6a0-5534c6fa14cf" />

- We can see it worked it. 

<img width="1046" height="489" alt="image" src="https://github.com/user-attachments/assets/1256863d-be49-462e-81b5-7aebc6b02af6" />

- Let's generate the script using the Poc generator and submit in the exploit server. 

- First we have to inject csrf key into user's session(Http header injection). For that we have to another parameter to inject in the header. 

<img width="895" height="440" alt="image" src="https://github.com/user-attachments/assets/84403d25-e264-4529-a5c0-1daa89d3ce50" />

<img width="1114" height="467" alt="image" src="https://github.com/user-attachments/assets/bb4c3bf5-4c8b-46c9-82d8-7f3d271a7276" />

- Let's add the csrfkey in the search term. we need to set-cookie of the csrfkey value as the attackers account. 

<img width="1067" height="615" alt="image" src="https://github.com/user-attachments/assets/77bfe176-13ec-4920-9570-750caa5ead75" />

- We can able to successfully inject that now we have to generate the script using the Poc generator. Here instead of submitting the form automatically we will try to set the cookie as csrfkey in the image and fails it will submit the form.  

<img width="1227" height="507" alt="image" src="https://github.com/user-attachments/assets/fe018dbb-300a-419f-b996-ac56b70467e9" />

- Hence by uploading the script we solve the lab. 

<img width="1100" height="440" alt="image" src="https://github.com/user-attachments/assets/7bbf9a4a-7f40-48e1-af9a-2967875c1188" />

# ------------------------------------------------------------------------------

# 6. CSRF where token is duplicated in cookie

<img width="761" height="184" alt="image" src="https://github.com/user-attachments/assets/8f7d239d-c79d-4feb-9853-ba3f4a7780d3" />

# Goal :  Use exploit sever to host an html page that uses CSRF attack to change the email address.

# Ingrediants : Same as above.

# Solving :

- Let do the usuals as the previous lab.

<img width="815" height="510" alt="image" src="https://github.com/user-attachments/assets/c487d7c5-3d53-4c87-ad97-91e1e7f1b2f7" />

<img width="936" height="458" alt="image" src="https://github.com/user-attachments/assets/dbf7cc3e-6657-4668-b254-31fc9d18fd0a" />

<img width="1028" height="398" alt="image" src="https://github.com/user-attachments/assets/afe3e554-cc91-46f1-bb5b-f831e45f10b8" />

- And we can notice that both the csrf key and token are the same value and when we checked with the dummy random value we see the 200 response from this we can understand that it doesn't matter value which value is the csrf token or key as long as both are euqal.

- Hence we can follow the previous lab steps and solve this.

 <img width="1162" height="587" alt="image" src="https://github.com/user-attachments/assets/38444a05-b9a0-42fb-9c06-3b28c1b30b68" />

 <img width="1220" height="455" alt="image" src="https://github.com/user-attachments/assets/9147ba33-7a42-4a71-b077-6cf439a5eab1" />

 - Hence by uploading the following we solve the lab. 

 <img width="1074" height="381" alt="image" src="https://github.com/user-attachments/assets/30775e18-a3ea-4bde-908b-1d5440490062" />

# ------------------------------------------------------------------------------


# 7. SameSite Lax bypass via method override.

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/d6f35bc4-a9ac-4c22-a49c-4ec3deeb1bdf" />

# Goal :  Same as above. 

# Ingrediants : Same as above.

# Solving :

- Same site Lax : It's cookie setting that limits when a browser sends a cookie to another site.

- Let's do the usuals. We can see there is no csrf token used.

<img width="962" height="495" alt="image" src="https://github.com/user-attachments/assets/81d8ddf2-d56a-44a9-a0bf-4cd752016a6b" />

- Since most same site - lax will block the cross site post requests. But when we checked the login post request it is sending the session cookie with the expiry time. Hence it will allow to send the cookie with the expiry date that it is vulnerable parameter we are going to exploit. 

<img width="1067" height="533" alt="image" src="https://github.com/user-attachments/assets/d31993f7-17d4-40c0-9109-5f95a8fa5832" />

<img width="1339" height="573" alt="image" src="https://github.com/user-attachments/assets/58b20419-e74e-481d-90c4-1cd5598ec0c0" />

-  We will try to change the request type and exploit this and it says method is not allowed. 

<img width="980" height="409" alt="image" src="https://github.com/user-attachments/assets/130adcee-80eb-4813-a034-1a2d57b94946" />

- We can change the method type by a concept called method spoofing where a hidden parameter will get as our desired request method type by using _method parameter.  

<img width="967" height="426" alt="image" src="https://github.com/user-attachments/assets/e3deaf12-f3d6-48bb-85e8-166fcb6402c0" />

- Let's generate the script with the method spoofing.

<img width="973" height="320" alt="image" src="https://github.com/user-attachments/assets/4f706cc0-9c0c-492a-ac09-d659883fa766" />

<img width="1080" height="464" alt="image" src="https://github.com/user-attachments/assets/745e5183-cd12-4454-b345-cd0453ee8be5" />

-  Hence by uploading this we solve the lab.

<img width="1303" height="488" alt="image" src="https://github.com/user-attachments/assets/297781b5-4f35-4891-a3a6-51116d891833" />

# ------------------------------------------------------------------------------

# 8. SameSite Strict bypass via client-side redirect.

<img width="753" height="135" alt="image" src="https://github.com/user-attachments/assets/c6eb506c-fd47-4e88-b93d-144b539e7b2d" />

# Goal :  Same as above. 

# Ingrediants : Same as above.

# Solving :

- In this lab it is using the same site stict where cookie will be only sent for the same site request.

<img width="992" height="567" alt="image" src="https://github.com/user-attachments/assets/b311bf4f-43eb-4508-856a-8321e1f9fcb2" />

- We can see even when changing the request method in the email change request we still get the 302 response. 

<img width="992" height="567" alt="image" src="https://github.com/user-attachments/assets/a7a9d6dd-4342-4507-aa9e-46ab31a5f95a" />

<img width="921" height="518" alt="image" src="https://github.com/user-attachments/assets/8d271f22-7139-40eb-a41c-12f2bea8006e" />

- We will try to post someting and watch the redirection. 

<img width="914" height="626" alt="image" src="https://github.com/user-attachments/assets/6a635d65-3fc8-4288-8cb1-9dba60d1ea56" />

<img width="1014" height="518" alt="image" src="https://github.com/user-attachments/assets/64847ffb-1ebe-4f76-882a-3e8f2a484f15" />

- It is using the js for this redirection

<img width="1034" height="485" alt="image" src="https://github.com/user-attachments/assets/cefed79f-7d87-40a5-ae35-a430a0e1b607" />

- It is getting the postId parameter from the /post/comment/confirmation?postId=4 and redirecting to page which is after the ? parameter. 

<img width="1107" height="543" alt="image" src="https://github.com/user-attachments/assets/0fc2d736-8470-485f-a96f-71a76c6382a8" />

<img width="950" height="398" alt="image" src="https://github.com/user-attachments/assets/794defe3-785a-4099-87aa-fd276e2ca44e" />

<img width="1108" height="516" alt="image" src="https://github.com/user-attachments/assets/75c55a5d-46eb-42a6-a733-69f7f4cf7a45" />

- We can see it is successfully redirected now we will change the payload to our desired page. 

<img width="948" height="535" alt="image" src="https://github.com/user-attachments/assets/86ab8d9a-c28d-463f-ba9d-9dfe774b6728" />

- We can see we got a "not found" error that is because it is under the section of post/ to overcome this we have to go before the preious folder by modifying the payload to this ../PostId. 

<img width="1163" height="606" alt="image" src="https://github.com/user-attachments/assets/84494d56-14c5-4d17-a348-8c04b7ad36ae" />

<img width="1021" height="330" alt="image" src="https://github.com/user-attachments/assets/d1a081f9-c20c-4db6-9d1f-06e4ea70e4f1" />

- We can see it is successfully redirecting. 

<img width="1082" height="510" alt="image" src="https://github.com/user-attachments/assets/7580f43d-1744-4458-b7ed-bea636006bc2" />

<img width="962" height="605" alt="image" src="https://github.com/user-attachments/assets/9d0456f0-5653-49bd-9a88-915c7517b9de" />

- Now we will append the change email get request and see is the email is changed or not. It says missing parameter that is beacuse we can encode the & to %26

<img width="1322" height="376" alt="image" src="https://github.com/user-attachments/assets/774ea44c-4f62-4208-bcc0-2aeccc2f2c4a" />

 <img width="1091" height="498" alt="image" src="https://github.com/user-attachments/assets/76f50b49-2b67-4dfb-bd8e-8404d4b508c8" />

 <img width="1042" height="654" alt="image" src="https://github.com/user-attachments/assets/c13fe150-4cb9-46a4-862f-4248a20e2ff5" />

- It worked we can able to change the email by the payload.  

<img width="858" height="445" alt="image" src="https://github.com/user-attachments/assets/e024f6b8-c191-45aa-884c-498119c2e063" />

- Now we will upload the script in the exploit server. 

<img width="1248" height="486" alt="image" src="https://github.com/user-attachments/assets/b984baf1-05f9-4bbc-bb9a-8dd4cdd0fa7e" />

- We successfully solved the lab after uploading this script.

<img width="1144" height="442" alt="image" src="https://github.com/user-attachments/assets/7523e045-010d-465a-99a9-c9f440e6885c" />

# ------------------------------------------------------------------------------


# 9. SameSite Strict bypass via sibling domain. 

<img width="764" height="253" alt="image" src="https://github.com/user-attachments/assets/a38fb175-70d7-4a80-b1d2-e59a21e6232e" />

# Goal : To perform CSWSH attack that exfiltrates the victim's chat history to the default Burp Collaborator server. Where the chat history contains login credentials in plain text. 

# Ingrediants :  Live chat, my-account view details and exploit sever button. 

<img width="1216" height="566" alt="image" src="https://github.com/user-attachments/assets/976a0058-7f5a-47c5-9b57-c9fedb037008" />

# Solving :

- Cross-site WebSocket hijacking : It is like a csrf but for a web socket. In this attack where attacker uses victims loggined account to open a websocket connection to a trusted website and perform actions for victim.

- When we using the live chat function and send a message we can see it is making a web socket connection and the messages are seen in the web socket history. 

<img width="1255" height="480" alt="image" src="https://github.com/user-attachments/assets/1a63b248-41c2-4d41-b41c-9bda6c8c4ed8" />

<img width="883" height="485" alt="image" src="https://github.com/user-attachments/assets/2783e0d3-ff54-4344-9461-8ccadc859779" />

- When we check the chat request we can see it is swicthing protocal and making a web socket connetion and there is no csrf token used. Hence it is vulnerable to csrf.

<img width="867" height="525" alt="image" src="https://github.com/user-attachments/assets/bc724ab4-3ba9-4281-88c4-8e58d4fd1a5b" />

- We will see the js file which is responsible for the exfiltrating the messages. This is js file which is responsible for the exfiltration. 

<img width="1200" height="409" alt="image" src="https://github.com/user-attachments/assets/a78320e4-fb3e-499d-b111-9ec80537549d" />

- They initiating the new web socket. 

<img width="1343" height="481" alt="image" src="https://github.com/user-attachments/assets/6ddf69ac-9a0f-4a98-aff1-40985ba7a19b" />

- There is an event handler to open the web socket. 

<img width="1071" height="351" alt="image" src="https://github.com/user-attachments/assets/25e5b959-95c4-4313-8e6a-edd2086425d2" />

- Let's develop the script that would reveal the exfiltration.

<img width="1199" height="398" alt="image" src="https://github.com/user-attachments/assets/06fe7856-d16f-4012-8eda-cfaeaa79ebeb" />

- When we see the access log we notice it has the base64 encrypted string. 

<img width="1358" height="453" alt="image" src="https://github.com/user-attachments/assets/b474a3d9-a1bc-4ec0-9921-4761b859ffe2" />

- When we decrypt the string it reveals that it has the chat messages. 

<img width="1365" height="386" alt="image" src="https://github.com/user-attachments/assets/1e1b3cf1-445d-41c7-a430-3d4c4d10fe2d" />

- We can see that this chat.js is loading an login page. 

<img width="1279" height="536" alt="image" src="https://github.com/user-attachments/assets/0eace45d-9b2f-4bdd-9bee-d521b1091b9b" />

- When going back and see the chat.js response it is loading one url. 

<img width="1337" height="528" alt="image" src="https://github.com/user-attachments/assets/9bc09311-5c81-41f8-9b06-07ae9176d41a" />

- When we load the url in the url we can see it loads a login page and we will inject the script there. 

<img width="811" height="285" alt="image" src="https://github.com/user-attachments/assets/39ec6a7a-41a6-439f-9980-839795f658b3" />

<img width="1273" height="512" alt="image" src="https://github.com/user-attachments/assets/ea11f506-3bf5-42db-8035-02b81ce1363e" />

- Let's change the request method and see the response it gives the 200 response only. 

<img width="1046" height="527" alt="image" src="https://github.com/user-attachments/assets/441664d4-61d1-4636-ba6e-3769384f9b99" />

- Now we will upload our payload in the get mathod query parameter.

<img width="1331" height="337" alt="image" src="https://github.com/user-attachments/assets/074cc401-742e-4a22-93a0-5c0da3ca87bb" />

- We can see the payload is decrypted in the response. 

<img width="1336" height="472" alt="image" src="https://github.com/user-attachments/assets/70c60760-881f-448e-93e3-596c9525cc85" />

- Let's upload the payload to the exploit server and fetch the password.

<img width="1314" height="530" alt="image" src="https://github.com/user-attachments/assets/a704d066-f4db-4d55-b19d-b4be47b6f3e0" />

- Let's decrypt the strings.

<img width="826" height="327" alt="image" src="https://github.com/user-attachments/assets/f6c32dfb-d474-4db0-9d90-a940f7624611" />

- Hence by using the password we loginned and solved the lab. 

<img width="1000" height="506" alt="image" src="https://github.com/user-attachments/assets/87926cc7-2d79-4502-a179-e96449ee2b5f" />

# ------------------------------------------------------------------------------

# 10. SameSite Lax bypass via cookie refresh

<img width="806" height="206" alt="image" src="https://github.com/user-attachments/assets/3dd48901-f880-48c5-bd50-391f04bb395d" />

# Goal : To exploit the csrf vulnerberality and change the victim's email address.

# Ingrediants : Home, my-account, view post and exploit server button.

# Solving :

- OAuth : It is way where one application access our data on another application without giving away our password.

- We will login in the Scoial media account.

<img width="883" height="491" alt="image" src="https://github.com/user-attachments/assets/357bb7ec-0a2e-48ff-89a6-7f2dd129a7f7" />

- So it can access our profile and now we will update our email. 

<img width="862" height="526" alt="image" src="https://github.com/user-attachments/assets/2c65c98f-7081-4946-ba17-8acb59c764f3" />

<img width="889" height="559" alt="image" src="https://github.com/user-attachments/assets/ad5edb2c-50aa-4f61-8dce-eccf93921046" />

- Let's modify the Csrf Poc script.

<img width="984" height="548" alt="image" src="https://github.com/user-attachments/assets/0d2f170a-d151-422f-9af2-1ff4638ab3f3" />

- When ever the user clicks anywhere on the screen it open up the pop up and refresh the Outh session cookie.

<img width="1091" height="468" alt="image" src="https://github.com/user-attachments/assets/e39d3cb6-ddf3-4a47-84c2-d8baced39248" />

- Hence first time we deliver the csrf script it will refersh the cookie and when we deliver the second time it will perform the csrf. And by doing that we solve the lab.

<img width="1224" height="481" alt="image" src="https://github.com/user-attachments/assets/38c65778-9518-40a5-9806-65809c5d7d16" />

# ------------------------------------------------------------------------------

# 11. CSRF where Referer validation depends on header being present

<img width="744" height="182" alt="image" src="https://github.com/user-attachments/assets/ba87287e-fe3b-436f-a9a7-adf0bb9f9708" />

# Goal : Same as above. 

# Ingrediants : Same as above. 

# Solving :  

- Let's update the email and see the response and see the response. 

<img width="1188" height="508" alt="image" src="https://github.com/user-attachments/assets/05b64463-50e7-4413-b822-c23ea59dc7ff" />

- We can notice it doesn't have the csrf token and referer and host are same domain. 

<img width="1022" height="400" alt="image" src="https://github.com/user-attachments/assets/7575ecd6-43ce-41c0-ac8a-9c3ce461b721" />

- Now let's take the referer and see the response. We can see even without the referer it is giving 302 response only. 

<img width="938" height="439" alt="image" src="https://github.com/user-attachments/assets/e18ca660-6e35-4939-b49f-e8490b6c24f2" />

- Let's generate the CSRF poc and test in the browser. 

<img width="613" height="468" alt="image" src="https://github.com/user-attachments/assets/eb408195-ca39-4973-9654-78f85b08b129" />

<img width="992" height="349" alt="image" src="https://github.com/user-attachments/assets/ec03d9fa-fc6d-48b8-ab04-96fd36137064" />

- It says "Invalid referer header" that is because the referer is different from the host domain

<img width="1020" height="353" alt="image" src="https://github.com/user-attachments/assets/2d31cfda-c1e9-422f-ae12-df891e194ee3" />
 
- Hence we will remove the header in the script and upload it to exploit server.

 <img width="932" height="497" alt="image" src="https://github.com/user-attachments/assets/0e24acb6-65a2-480e-9ad0-6d43d14abe03" />

- Hence we solved the lab by uploading the script to exploit server. 

<img width="1200" height="484" alt="image" src="https://github.com/user-attachments/assets/e5ab5d71-a139-4fb0-b570-4586a00fcf99" />

<img width="1149" height="481" alt="image" src="https://github.com/user-attachments/assets/f42d7aec-c642-4ace-978e-a959841bb3bd" />

# ------------------------------------------------------------------------------

# 12.


