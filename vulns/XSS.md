XSS or cross site scripting is classified as an injection attack where malicious JS gets injected into a web application with the intention of being executed by other users
# Reflected XSS
Reflected XSS happens when user-supplied data in a HTTP request is included in the webpage source without any validation. This is usually used in phishing to steal credentials from the webpage using stuff like embedded iframes
# Stored XSS
Stored xss is where the payload is stored on the web application and then gets run when other users visit the site or webpage
## Blind XSS
blind xss is a form of stored xss where the payload gets stored on the website for another user to view
# DOM XSS
DOM based cross site scripting is a type of xss where the client side JS running in the browser takes attacker controlled input and directly uses it to modify the dom in an unsafe way
# Polyglot XSS payload
```
jaVasCript:/*-/*`/*\`/*'/*"/**/(/* */onerror=PAYLOAD-HERE )//%0D%0A%0d%0a//</stYle/</titLe/</teXtarEa/</scRipt/--!>\x3csVg/<sVg/oNloAd=PAYLOAD-HERE//>\x3e
```
```
jaVasCript:/*-/*`/*\`/*'/*"/**/(/* */onerror=alert("hello"); )//%0D%0A%0d%0a//</stYle/</titLe/</teXtarEa/</scRipt/--!>\x3csVg/<sVg/oNloAd=alert("hello");//>\x3e
```