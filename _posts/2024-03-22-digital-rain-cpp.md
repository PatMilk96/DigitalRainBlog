---
layout: post
title: A Project in Modern C++
tags: cpp coding project
categories: demo
---

## Github Repository
https://github.com/PatMilk96/Digital_Rain-Patryk-Milkiewicz-
All coded in VisualStudio 2022


## Introduction

So, what is Digital rain? If you've watched The Matrix then you know what I'm talking about. It's the icon green rain of Japanese characters falling down the screen, and if you're a big fan of the movie there is a chance you got some good sushi recipes out of it!
My goal was to recereate this iconic simulation as close as possible using C++.
In this blog I will describe my thought process behind creating my digital rain, the technologies used the details of code implementation along with any issues I faced along the way. 

I started with the basics... By playing The Matrix digital rain on YouTube at 0.25 speed. I will refer to each string of verticaly falling characters as 'droplet' or 'droplets'. I must have spent a solid 10 minutes studying it, watching each droplet fall, and figuring out how it works. What I noticed is that a character is printed on the screen and then another new one, vertically just in front of it and so on. The droplets had a set size with the tail end slowly fading away. The droplets were also falling at different speeds. I focused on these characteristics of the droplet.

I kept it very simple at the beginning by creating a simple algorithm in my main.cpp file. This algorithm seen below creates a vector of characters and prints them out 1 by 1 on the screen, when it prints the whole vector it starts "removing" (just placing an empty character) at the tail end of the vector seen on the screen, it then goes to back to the beginning of the vector and starts printing the characters again.
It's a very simple algorithm and I based the whole project on that simple idea.

*note: the GoToXY() function simply goes to a position on the screen given the X and Y coordinate*

<img src="https://github.com/PatMilk96/DigitalRainBlog/tree/main/docs/assets/images/OriginalAlgorithm.jpg" width="450" height="400">
[img 1.1]

## Project Overview

The project consists of 3 files:

- main.cpp
- DigitalRain.cpp
- DigitalRain.h

**main.cpp**

In my main.cpp file I initialize a vector of droplets and put them in an infinite loop, iterating through each droplet.


**DigitalRain.cpp**

This is the file where all the magic happens. Here I initialize my default Rain object along with any setters, and my custom functions.
The key functions here are the *GoToXY()* which allows me to go to a certain X and Y coordinate on the screen to print a character in that exact position *SetSpeed()* function that finds how many objects are being initialized for the current window size and sets the appropriate speed, *GenerateRandomChars()* that uses a rand() function to generate a vector of random characters, *ReturnRand()* that I can call to return two integers so I can set a different random speed to a droplet once it has reached the end, *BottomReachedFunction()* that that starts removing characters from the tail end of the droplet and once all are removed it populates the vector with new characters, *Init()* that removes the cursor and then populates a vector of objects with my Rain droplets, finally we have the *Print()* function that prints out the vetors of characters from my droplets.


**DigitalRain.h**

In this file, I provide all my public function definitions and private variables

**Insert header file here**


## Design And Implementation

When printing to the console window it typically moves from left to right and when it reaches the end it moves down a position and continues left to right, which would mean that all my droplets would be falling from the same postions at the same speeds. By using the GoToXY() function I can print the characters in different positions to make it look more realistic. 




**Place this in Implementation Details**In the main.cpp file I initialize my Rain object (Rain rain;) that holds all the attributes for my droplet, then I initialize a vector of Rain objects called raindrops (std::vector<Rain> raindrops;), creating my droplets. After that, I have an infinite loop that iterates through my raindrops and prints them on the screen.



Font can be *Italic* or **Bold**.

Code can be highlighted with `backticks`.

Hyperlinks look like this [GitHub Help](https://help.github.com/).

A bullet list:

- vectors
- algorithms
- iterators

You can add an image that has been uploaded to the repository in a /docs/assets/images folder.


