---
layout: post
title: A Project in Modern C++
tags: cpp coding project
categories: demo
---

## Introduction

So, what is Digital rain? If you've watched The Matrix then you know what I'm talking about. It's the icon green rain of Japanese characters falling down the screen, and if you're a big fan of the movie there is a chance you got some good cooking recipes out of it!
I recreated this icon simulation using C++.
In this blog I will describe my thought process behind creating my digital rain, the technologies used the details of code implementation along with any issues I faced along the way. 

I started with the basics... By playing The Matrix digital rain on YouTube at 0.25 speed. I must have spent a solid 10 minutes studying it, watching each droplet fall, and figuring out how it works. What I noticed is that a character is printed on the screen and then another new one just in front of it and so on. The droplets had a set size with the tail end slowly fading away. The droplets were also falling at different speeds. I focused on these characteristics of the droplet.

I kept it very simple at the beginning by creating a simple algorithm in my main.cpp file. This algorithm seen below creates a vector of characters and prints them out 1 by 1 on the screen, when it prints the whole vector it starts "removing" (just placing an empty character) at the tail end of the vector seen on the screen, it then goes to back to the beginning of the vector and starts printing the characters again.
It's a very simple algorithm and I based the whole project on that simple idea.

*note: the GoToXY() function simply goes to a position on the screen given the X and Y coordinate*

<img src="https://github.com/PatMilk96/DigitalRainBlog/blob/main/docs/assets/images/OriginalAlgorithm.jpg" width="350" height="350">




Font can be *Italic* or **Bold**.

Code can be highlighted with `backticks`.

Hyperlinks look like this [GitHub Help](https://help.github.com/).

A bullet list:

- vectors
- algorithms
- iterators

You can add an image that has been uploaded to the repository in a /docs/assets/images folder.


