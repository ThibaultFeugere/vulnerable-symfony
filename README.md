# vulnerable-symfony

Vulnerable Symfony aims to make everyone aware of common OWASP Top 10 risks and other common issues that we encounter in business.

Symfony projects are relatively secure if : 

- you are up-to-date
- you don't have legacy code, or you are at least aware and maintain it
- you often test your product

Nota bene : this is why DevSecOps philosophy can be usefull. It provides support from the design of a feature to delivery.

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
  - Define [Length Constraint](https://symfony.com/doc/current/reference/constraints/Length.html)
  - Define [NotIdenticalTo Constraint](https://symfony.com/doc/current/reference/constraints/NotIdenticalTo.html)
- Check if password has been compromised ([NotCompromisedPassword](https://symfony.com/doc/current/reference/constraints/NotCompromisedPassword.html))

### 2. Cryptographic failure / Sensitive data exposure

#### Encrypt everything

You should encrypt all requests with TLS (v1.2 and v1.3) in order to avoid many attacks or data leak due to a [Man In The Middle](https://en.wikipedia.org/wiki/Man-in-the-middle_attack) for example. Even in dev mode !

TODO : 
- Known hash
- Symfony Password handler with ["auto hasher"](https://symfony.com/doc/current/security/passwords.html#the-auto-hasher)

### 3. Injections 

This happens when a user input is interpreted by the server.

#### SQL Injection

Make sure to use Doctrine ORM and check if you are using a [Doctrine SQLi safe API function](https://www.doctrine-project.org/projects/doctrine-dbal/en/current/reference/security.html). 

You shouldn't use concatenation and go for prepared statements to execute your queries.

#### OS Command Injection

This happens when a server-side code like PHP make a call to host machine.

TODO : add reverse shell

You should avoid using PHP functions such as `exec()` or `system()`.
If you really need to exec commands on the server, prefer [The Process Component](https://symfony.com/doc/current/components/process.html)

### 4. Insecure design

TODO : add real case about account locked and sms.

### 5. Security misconfiguration

- Default passwords
- Too much permissions ([Principle of Least Privilege](https://en.wikipedia.org/wiki/Principle_of_least_privilege))
- Overly detailed error messages
- Reveal too much details

### 6. Vulnerable and Outdated Components

Looks easy but many projects are behind schedule and the longer you wait the harder it is to upgrade.

TODO : add vulnerable and outdated component and exploit.

### 7. Identification and Authentication Failures

### 8. Software and Data Integrity Failures 

### 9. Security Logging and Monitoring Failures

### 10. Server-Side Request Forgery

## TODO :

- Add 403 to 404 best practice
- Add "why you should use TLS in dev environment"
- (not urgent) Add XML attacks 
- file upload on Symfony ?
