# MyBugbountyCheckList

# Password reset/forgot

- Password reset link not expiring
- No rate limiting on password reset
    > Start the burp suite and intercept the password reset request
    
    > Send to intruder
   
    > Use null payload

- Password reset token leak via referer
    > Request password reset to your email address
    
    > Open on the password reset link
    
    > Make sure you don’t change the password there
    
    > On Password Reset Page Click On Social Media Links Given Below And Capture The Request Using Burp Suite
    
    > Check if the referer header is a leaking password reset token?

- Password reset with manipulating email parameter
    
    > email=victim@xyz.tld&email=hacker@xyz.tld
       
    > email=victim@xyz.tld%0a%0dcc:hacker@xyz.tld
        
    > email=victim@xyz.tld,hacker@xyz.tld
    
    > email=victim@xyz.tld%20hacker@xyz.tld
    
    > email=victim@xyz.tld|hacker@xyz.tld
    
    > email=victim
    
    > email=victim@xyz
    
    > {“email”:[“victim@xyz.tld”,”hacker@xyz.tld”]}
   
- Password reset Poisoining leads to token leak
    > Host: attacker.comHost: target.com
    
    > X-Forwarded-Host: attacker.comHost: target.com
    
    > Host: attacker.com
   
# Oauth2 vulnerabilities

- Implicit-grant type vulnerable to manipulating emails 

- CSRF Improper handling of `state` parameter

- Weak validation of `redirect-uri` parameter to auth_code leak, xss, open redirects, etc.

- client_secret_key, access_token leaked

- Pre Account Takeover 
    > If the application does not require email verification on account creation, try creating an account with a victim’s email address and attacker password       before the victim has registered. If the victim then tries to register or sign in with a third party, such as Google, it’s possible the application           will do a lookup, see that email is already registered, then link their Google account to the attacker created account. This is a “pre account               takeover” where an attacker will have access to the victim’s account if they created it prior to the victim registering 

# JWT Authorization/Authentication bypass vulnerablities
-  Unverified signature bypass `changing value in payloads of jwt`

- Flawed signature bypass changing `alg` to `none`

- Weak Signing of key `HS256` 
    > Bruteforcing private key and resign the token 

- jwk/jku Header parameter injection in jwt 

- Kid header path traversal `HS256`

- Jwt algorithm confusion attacks
    > Retrieving jwt public key and converting into secret key format and changing `alg` to `HS256` for confusion

# CSRF/Clickjacking 
- On `my profile` sensitive action like `delete account, password/email change`

# File upload vulnerabilities 
- On profile pic, and others to `RCE, XXE, XSS,etc.`
 
