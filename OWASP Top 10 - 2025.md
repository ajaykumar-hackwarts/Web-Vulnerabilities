OWASP(Open Web Application Security Project ) is global non-profit foundation that provides resources and tool to ensure the web application security. OWASP top 10 is a list the top 10 overall threats/vulnerabilities happened in the last 3-4 years. 

As per recent updated the OWASP Top 10(2025) is. 

## 1. A01:2025 - Broken Access Control :-

It happpens when a web application fails to properly restricts what an user can access and do. 

Example : Login as a normal user and change to admin and get full access. 

## 2. A02:2025 - Security Misconguration :-

It happens when a web application, server or system set up in a way that leaves it exposed to attackers. 

Example : Reveals too much in error messages, outdated software, default credentials unchanges like password : password. 

## 3. A03:2025 - Software Supply Chain Failures :-

It introduced by the third party components, dependencies, software distribution systems. This happens due to blindly trusting third party dependencies and updates. 

Example : SolarWinds Attack(2020) where attacker breached solar windows update system and inserted malicious code therefore organization installed the backdoor through the legitimate updates. 

## 4. A04:2025 - Cryptographic Failures :-

It occurs when data meant to be protected is either not encrypted properly or use weak encryption. 

Example : A banking app stores users password in a plain text in a database if attacker access the database they can see and misuse the password. 

## 5. A05:2025 - Injection :-

It happens when untrusted/malicious data is sent to the interpreter(like database, command shell) as a part of command or query. simply it happens when the user input is directly passes it to an interpreter(database) without validation or sanitization. 

Example : When attacker typed ' OR '1'='1 into a live login form if it vulnerable immediately he will bypass authentication. 

## 6. A06:2025 - Insecure Design :-

It happens when application architecture, threat modelling or design decision is itslef lack security. 

Example : High value admin dashboards design without 2FA and attacker performs unlimited brute-force password attempts without restriction due to poor design.

## 7. A07:2025 - Authentication Failures :-

It occurs when an application's authentication system is implemented poorly or incompletely allowing attackers to bypass credentials easily. 

Example : Weak password policy, broken MFA implementation like sms otp accepted after resue. 

## 8. A08:2025 - Software or Integrity Failures :-

It happens when software updates, critical data are failed to ensure integrity. It's about trusting updates that aren't verified or protecting from unauthorized modification. 

Example : Application loads plugins or modules without verifying the digital signatures. 

## 9. A09:2025 - Security Logging and Alerting Failures :-

It happens when an application don't properly log security related-events or fail to alert or monitor these events effectivley. 

Example : No logging for failed logins so attacker can brute-force attacks for days. No Tamper protection so user can modify logs. 

## 10. A10:2025 - Mishandling of Exceptional Conditions :-

It happens when an application is fails to handle errors, exceptions or unusual conditions. Instead of failing safely, the system may expose sensitive information or behave unpredicably. 

Example : Banking App API crash(2022) : API crashes during high traffic due to null pointer exceptions and the attacker transferring move money from the bank due to poor error handling. 
