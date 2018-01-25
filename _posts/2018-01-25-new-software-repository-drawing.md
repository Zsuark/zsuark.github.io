---
layout: post
title:  "New Software Repository Available: Drawing"
date:   2018-01-25 06:30:00 +0100
categories: "demo software"
tags: ["software development", "Clojure", "Quil", "drawing", "animation", "demo software", "JavaFX"]
---

# New Software Repository Available: Drawing

Just a quick blog post this week. I finished doing all the little tasks to put a new software repository on GitHub: [Drawing](https://github.com/Zsuark/drawing).

Drawing is a collection of animated drawings made with Clojure and Quil. The sketches are of fractals, and miscellaneous ideas. I also used JavaFX to create a menu window as a launcher for the various sketches. I had never used JavaFX until yesterday, so I'm pleased I could even learn and translate this basic usage into Clojure. After all, Clojure is still new to me too.

There will be upcoming blog posts discussing the techniques, weaknesses and how we can make things better. For example, we can talk about calculating angles, memoisation, code structure and layout, etc. So play and check out future blog posts to see what is in store.


# Software Quality

The software itself is far from perfect &mdash; but it works. We can always streamline, optimise and rewrite code for greater clarity or to meet other goals. The fact a piece of software works is the main thing.

There are ways to break the software. For example, using the quit keyboard shortcut with a sketch open. There are other problems, such as the word "Applet" appearing as the title of the sketches rather than what I specify in the code, and so forth.

Additionally, I have mis-labelled some of the fractal curves - I discovered some for myself via happy accidents, and I didn't know what to call them. I will be correcting this shortly.

For the most part, the sketches all work within reasonable time. Some, such as the dragon curves, do take a long time to calculate and display. In a future post we will look at what we can do about this.

So the software is not perfect, but it does the job I want it to.


# Pragmatic Programming

One thing you may notice is that there is no testing. Well, this is one of those times where it either works, or it doesn't, and it is clear. I am not sure how I'd automate testing for this, as after all, it is visual software &mdash; my eyes test it. Also, the software does not have too many components, so manual testing isn't unreasonable. If the software continued to grow, I would have to reconsider this approach.

I consider myself a pragmatic programmer. To me that means that I try to adhere to the [principles of Agile](http://agilemanifesto.org/) rather than strict tenants of certain Agile methodologies, such as Test Driven Development (TDD). This is does not mean that I do not or will not use TDD when necessary or desired. I just do not find it necessary here. Any TDD purists who disagree with me, are welcome to **show** me how it would be better in this case. (Really, I would genuinely like that.) :smile:


# That's it for this week

Feel free to play with and comment on the software. Come back next week for more software development goodies.
