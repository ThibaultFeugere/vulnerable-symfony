# vulnerable-symfony

Vulnerable Symfony aims to make everyone aware of common OWASP Top 10 risks and other common issues.

## Top 10 OWASP

OWASP organization update regularly most critical security risks to web applications.

![image](https://user-images.githubusercontent.com/32579584/222953149-f45f4937-b01b-4902-be77-a13deb4c0380.png)

### 1. Broken Access Control

Broken access control or broken authentication is about core component of applications. Their goal is to verify your identity, very often in order to grant access.

#### Brute force

TODO : add flaw in incoming symfony project.

Patch : 
- Captcha (warning ⚠ : many captchas aren't integrated correctly. If they are, [they can still be bypassed](https://www.youtube.com/watch?app=desktop&v=1CeUu8j7xsQ&ab_channel=Underscore_))
- Rate limiter (defence in depth)
- Two-factor authentication ([also block brute force](https://symfony.com/bundles/SchebTwoFactorBundle/6.x/brute_force_protection.html#2-block-authentication))
- Notify the victim 
- Setup trusted model

#### Weak credentials

This allows attackers to login without brute force or even dictionary.

Patch : 
- Define password policy (with [constraints](https://symfony.com/doc/current/reference/constraints.html))
- Check if password has been compromised ([NotCompromisedPassword](https://symfony.com/doc/current/reference/constraints/NotCompromisedPassword.html))

### 2. Cryptographic failure / Sensitive data exposure

### 3. Injections 

This happens when a user input is interpreted by the server.

- SQL Injection
- Command Injection

#### OS Command Injection

This happens when a server-side code like PHP make a call host machine.
TODO : add reverse shell

### 4. Insecure design

TODO : add real case about account locked and sms.

### 5. Security misconfiguration

### 6. Vulnerable and Outdated Components

TODO : add vulnerable and outdated component and exploit.

### 7. Identification and Authentication Failures

### 8. Software and Data Integrity Failures 

### 9. Security Logging and Monitoring Failures

### 10. Server-Side Request Forgery

## TODO :

- Add 403 to 404 best practice
- Add "why you should use TLS in dev environment"
