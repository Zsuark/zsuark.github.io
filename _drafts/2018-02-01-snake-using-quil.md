---
layout:   post
title:    "Snake using Quil"
date:     2018-02-01 06:30:00 +0100
category: games
tags:     ["software development", "games", "clojure", "quil"]
---

# Snake

[Snake](https://en.wikipedia.org/wiki/Snake_(video_game_genre)) is an old video game, variants of the game were also known as Nibbler and Snake Byte amongst others. You may remember it from your microcomputer days (if you are old enough) or your old Nokia mobile phone.

Within the game the user must navigate the snake around the screen using the arrow keys. If the snake runs into a wall or itself, the game ends.

The goal is to direct the snake to eat as many apples as possible. However, as the snake eats apples it grows in length, making the game increasingly difficult.

You can find a simple version of the game I have completed within my [drawing repository on GitHub](https://github.com/Zsuark/drawing)

# ClojureScript demo

{% include snake.html %}

Use the arrow keys to control the snake. The canvas element needs focus - so click on game if the controls aren't working.

