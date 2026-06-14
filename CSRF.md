# CSRF(Cross Site request forgery) : Attacker tricks the victim's browser into sending unarthorized requests to trusted website where user is already authenticated. 

- Session cookie is saved by the browser.
- Attcker send a malicious csrf script link through WhatsApp, Telegram, SMS, or social media.
- When victim clicks the link and when the the page is loaded the script will be executed 
- Since the user is already authenticated, the browser automatically includes the session cookie.
- The target website recieves what appears to be legitimate requests from the autorised user and it may perform action if CSRF protection is not there.

# 1. CSRF vulnerability with no defenses  :

