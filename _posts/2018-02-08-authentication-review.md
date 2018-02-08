---
layout:   post
title:    "Authentication and Security review"
date:     2018-02-08 06:30:00 +0100
category: architecture
tags:     ["software development", "software architecture", "JWT", "authentication", "security", "Clojure"]
---

# Authentication and Security Review

This last week, I have been doing a lot of research/review and experimentation with authentication, security and databases. So, this week's blog posts are more of a "brain dump" than proper articles.

Just to remind you we are currently building a social media application using Clojure and Ring.


# Mobile and Web Application Security

Mobile and web apps have their processing divided between the front-end (web page, mobile app) and the back-end services.

Communication between the front-end and the back-end is done over HTTPS, in order to secure the communication. However, it doesn't ensure the identity of the user.

A user may authenticate themselves with a username/password or via OAuth2 (e.g. FaceBook, Twitter, or other single sign-on service). From there the authentication server supplies the front-end application with a security token &mdash; specifically a Java Web Token (JWT).

The token is stored by the front-end application and allows it to securely authenticate itself to the back-end services. Using this system eliminates the overhead of session management, as tokens are self-contained and verifiable by individual services.


# Relevant Clojure libraries

- [buddy](https://github.com/funcool/buddy)
- [friend](https://github.com/cemerick/friend)
- [yada](https://github.com/juxt/yada)

Of the options above, it appears &mdash; at least for the moment &mdash; that **buddy** is a good fit for what we are trying to achieve, and has a lot of documentation and support (vendor supplied and informal blogs, etc).


# Sample Reading list

- [Introduction to JSON Web Tokens](https://jwt.io/introduction/)
- [5 Easy Steps to Understanding JSON Web Tokens (JWT)](https://medium.com/vandium-software/5-easy-steps-to-understanding-json-web-tokens-jwt-1164c0adfcec)
- [JSWON Web Token (Wikipedia)](https://en.wikipedia.org/wiki/JSON_Web_Token)
- [Single sign-on (Wikipedia)](https://en.wikipedia.org/wiki/Single_sign-on)
- [Securing Clojure Microservices using buddy - Part 1: Creating Auth Tokens](http://rundis.github.io/blog/2015/buddy_auth_part1.html)
- [Mobile API security techniques](https://www.approov.io/blog/mobile-api-security-techniques-part-2.html)
- [Security in mobile APIs: OAuth 2.0 vs basic HTTP access authentication](https://bbvaopen4u.com/en/actualidad/security-mobile-apis-oauth-20-vs-basic-http-access-authentication)
- [The Ultimate Guide to Mobile API Security](https://stormpath.com/blog/the-ultimate-guide-to-mobile-api-security)
- [Mobile API Security Techniques](https://hackernoon.com/mobile-api-security-techniques-682a5da4fe10)
- [Using JSON Web Tokens with Clojure](http://www.bradcypert.com/using-json-web-tokens-with-clojure/)
- [Speak friend and enter! Authenticating web requests with yada](https://juxt.pro/blog/posts/yada-authentication.html)
- [Clojure auth with buddy](https://adambard.com/blog/clojure-auth-with-buddy/)
- [OAuth2 is easy - illustrated in 50 lines of Clojure](https://leonid.shevtsov.me/post/oauth2-is-easy/)
- [SPA best practices](https://stackoverflow.com/questions/20963273/spa-best-practices-for-authentication-and-session-management)
- [Google Mobile App Best Practises](https://developers.google.com/identity/work/saas-mobile-apps)


# That is all...

..for the moment &mdash; except also check out the [quick review of databases](/architecture/2018/02/08/database-and-graph-theory-review/) that I have been doing this week.