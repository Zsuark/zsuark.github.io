---
layout:   post
title:    "Secure Authentication with Buddy"
date:     2018-01-11 16:00:00 +0100
category: personal
tags:     ["software development", "Clojure", "buddy", "security", "authentication", "JWT"]
---

# Secure Authentication with Buddy

[Buddy](https://github.com/funcool/buddy) is an awesome security library for Clojure. It provides both lower-level and higher-level security functions.

Regardless of whichever libraries used, it is still important to have a base understanding of what is happening, and to make wise decisions.

For example, always using a salt when hashing passwords and ensure you hashing algorithm is contemporary and trust-worthy. I think this step is often skipped over glossed over too quickly when building systems. However, if you want to make robust systems is is very important.

The long list of algorithms and processes for security is daunting. So, take a deep breath and do your best.

The truth of the matter is, that nothing is ever totally secure. If you have a secret you absolutely must keep, then don't ever tell anyone. Everything else is risk mitigation.


# Sample readings &mdash; password hashing
- [The Open Web Application Security Project](https://www.owasp.org/index.php/Main_Page)
- [OWAP - Password Storage Cheat Sheet](https://www.owasp.org/index.php/Password_Storage_Cheat_Sheet)
- [Do any security experts recommend bcrypt for password storage?](https://security.stackexchange.com/questions/4781/do-any-security-experts-recommend-bcrypt-for-password-storage)
- [Salted Password Hashing - Doing it Right](https://crackstation.net/hashing-security.htm)
- [Password Hashing: PBKDF2, Scrypt, Bcrypt](https://medium.com/@mpreziuso/password-hashing-pbkdf2-scrypt-bcrypt-1ef4bb9c19b3) - good explanation, unsure of actual advice
- [Clojure auth with buddy](https://adambard.com/blog/clojure-auth-with-buddy/)

Buddy's buddy-hashers password checking system appears to use password salts appropriately. I checked the source code for this.

OWASP recommends Argon2 the best hashing algorithm, buddy has yet to implement this. However, the choices buddy provides are robust. I would recommend further selecting the best hashing techniques buddy provides according to known information.


# Game-plan

- Start easy, "hard code" usernames and passwords into the software (ONLY for now)
- Get basic authentication with this 
- Get JWT token issuing and use working
- Choose hashing strategy and lock down username/password log-in system
- Configure database storage of usernames and passwords
- **Remove all** user/password combinations stored directly in the code
  - Exception: running automated tests
  - Ensure that no live system is left vulnerable