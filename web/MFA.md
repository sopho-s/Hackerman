MFA typically combines two or more different kinds of credentials from the categories: something you have, something you know, something you are, somewhere you are, and something you do
# Common vulns in MFA
## Weak OTP generation algorithms
The security of a one-time password is only as strong as the algorithm used to create it. if the algorithm is weak or too predictable, it can make the attacker's job easier trying to guess the OTP
## Application leaking the 2FA token
If an applicaiton handles data poorly or has vulnerabilities like insecure API endpoints, it might accidentally leak the 2FA token in the application's HTTP response
Due to insecure coding, some applications might also leak the 2FA token in the response
## Brute forcing the OTP
if an attacker has unlimited guess and has not rate limiting it may make it very easy to brute force the OTP 
# OTP leakage
The OTP leakage in the XHR (XMLHttpRequest) response typically happens due to poor implementations of the 2FA mechanism or insecure coding. common reasons why this happens are:
## Server-side validation and return of sensitive data
In some poorly designed applications, the server validates the OTP, and rather than just confirming the success or failure, it returns the OTP in the response
## Lack of proper security practices
developers might overlook the security implications of exposing sensitive information like OTP in the API responses. This often happens when developers are focused on making the application functional without considering how attackers could exploit these responses
## Debugging information left in production
during development or testing phase, developers might include detailed debugging information in responses to help diagnose issues. If these debug responses are not removed before deploying to production, sensitive information like OTPs could be exposed
# Insecure coding
In some applications, flawed logic or insecure practices can lead to a situation where critical parts of the application can be accessed without fully completing the authentication process. specifically an attacker might be able to bypass the 2FA mechanism entirely and gain access to the dashboard or other sensitive areas without entering the OTP

**https://book.hacktricks.wiki/en/pentesting-web/rate-limit-bypass.html**