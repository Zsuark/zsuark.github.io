---
layout: post
title:  "New Software Repository Available: drawing"
date:   2018-01-25 06:30:00 +0100
categories: "demo software"
tags: ["software development", "Clojure", "Quil", "drawing", "animation", "demo software", "JavaFX"]
---

# New Software Repository Available: drawing

Just a quick blog post this week. I finished doing all the little tasks to put a new software repository on GitHub: [drawing](https://github.com/Zsuark/drawing).

It is a collection of drawings made with Clojure and Quil. The sketches are of fractals, and other animated drawings. I also used JavaFX to create a menu window as a launcher for the various sketches. (I had never used JavaFX until yesterday, so I'm pleased I could even translate the usage into Clojure.)

There will be upcoming blog posts discussing the techniques, and looking at the techniques used, weaknesses and how we can make things better. For example, we can talk about calculating angles, memoisation, code structure and layout, etc. So play and check out this blog next week to see what is in store.

# Software Quality

The software itself is far from perfect &mdash; but it works. We can always streamline, optimise and rewrite code for greater clarity or to meet other goals. The fact a piece of software works is the main thing.

It all works within reasonable time, however some of them (like the dragon curves) take a long time to calculate and display. More on that in a future post.


# Pragmatic Programming

One thing you may notice is that there is no testing. Well, this is one of those times where it either works, or it doesn't, and it is clear. I am not sure how I'd automate testing for this, as after all, it is visual software. My eyes test it.

I consider myself a pragmatic programmer &mdash; that means, I try to adhere to the [principles of Agile](http://agilemanifesto.org/) rather than strict tenants of certain Agile methodologies, such as Test Driven Development (TDD). This is does not mean that I do not or will not use TDD when necessary. It's just not necessary here.


# That's it for this week

Feel free to play with and comment on the software. Come back next week for more software development goodies.
