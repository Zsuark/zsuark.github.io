---
layout:   post
title:    "Summary of past week (or so)"
date:     2018-03-06 16:00:00 +0100
category: update
tags:     ["security","arangodb","https","ring","compojure","compojure-api"]
---

# Summary of past week

So, I meant to send this blog post out last Thursday, but missed it by accident! This is a bit of a round-up of what has been happening in that last week before then.

My little project to create a secure back-end service ready for SPA and mobile applications is going nicely.

# Current state of technology stack

- Clojure 1.8.0 
- [Compojure-api](https://github.com/metosin/compojure-api) 2.0.0-alpha18 &mdash; must/should use 1.1.11 in production until 2.0.0 is ready?
- TODO: Lookup Clojure.spec
- [clj-time] - for date/time functionality. "A date and time library for Clojure, wrapping the Joda Time library."
- [Arango](https://www.arangodb.com/)  3.3.3 - [Documentation:
Find manuals for ArangoDB, AQL, Foxx and many other useful resources](https://www.arangodb.com/documentation/)
- [buddy](https://github.com/funcool/buddy) 2.0.0 "Buddy &mdash; Security library for clojure."
	- [buddy/buddy-auth "2.1.0"](https://github.com/funcool/buddy-auth) &mdash; _buddy-auth_ module is dedicated to provide **Authentication** and **Authorization** facilities for ring and ring based web applications.
	- [buddy/buddy-hashers "1.3.0"](https://github.com/funcool/buddy-hashers) &mdash; _buddy-hashers_ module is dedicated to provide a collection of secure password hashers functions.
	- [buddy/buddy-sign "2.2.0"](https://github.com/funcool/buddy-sign) &mdahs; _buddy-sign_ module is dedicated to provide a high level message signing.

TODO: Investigate using Clojure 1.9.0 (Latest since: the 8th December 2017)
  
# Security concern - username/password in URL

Clarango doesn't natively connect to Arango, but via the HTTP interface. As such, the URL contains the 

[Clarango &mdash; A Clojure Driver for ArangoDB](https://github.com/Lepetere/clarango)

[Are secret URLs secure over HTTPS](https://security.stackexchange.com/questions/33738/are-secret-urls-secure-over-https)

[Can URLs be sniffed when using SSL](https://security.stackexchange.com/questions/30976/can-urls-be-sniffed-when-using-ssl)

[Are URLs viewed during HTTPS transactions to one or more websites from a single IP distinguishable?](https://security.stackexchange.com/questions/4388/are-urls-viewed-during-https-transactions-to-one-or-more-websites-from-a-single)

So, the URL is fine. 

# Other security consideration - logging

However, what about logs?

How secure are your logs? What is being recorded in them?

Logs are important to be written quickly, so it isn't always practical to store
encrypted logs. (You could always encrypt your filesystem, but this again has performance hits.)

So, my conclusion is that whilst sending username/password information as part of an HTTPS request may be secure, doing so may not be the best idea.

Whenever I use Clarango I notice that the entire connection string is logged to standard output. When the username and password forms part of the URI, this is not a good idea. I cannot see anything in the documentation on how to turn on/off this feature.

 - If there is a security breach where someone manages to steal the logs, then they have the ability to see the database username and password.
 - You do not wish to have administrators, other system users or casual observers to see such sensitive information.

I need to resolve this somehow, before deploying to production.

# That is all...

Short and sweet...  speak to you again soon!