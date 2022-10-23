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
