---
layout: post
title: A Project in Modern C++
tags: cpp coding project
categories: demo
---

## Github Repository
https://github.com/PatMilk96/Digital_Rain-Patryk-Milkiewicz-
All coded in VisualStudio 2022


<img src="https://raw.githubusercontent.com/PatMilk96/DigitalRainBlog/main/docs/assets/images/DigitalRain2.gif" width="1000" height="650">


## Introduction

So, what is Digital rain? If you've watched The Matrix then you know what I'm talking about. It's the icon green rain of Japanese characters falling down the screen, and if you're a big fan of the movie there is a chance you got some good sushi recipes out of it!
My goal was to recreate this iconic simulation as closely as possible using C++.
In this blog I will describe my thought process behind creating my digital rain, the technologies used the details of code implementation along with any issues I faced along the way. 

I started with the basics... By playing The Matrix digital rain on YouTube at 0.25 speed. I will refer to each string of vertically falling characters as 'droplet' or 'droplets'. I must have spent a solid 10 minutes studying it, watching each droplet fall, and figuring out how it works. What I noticed is that a character is printed on the screen and then another new one, vertically just in front of it, and so on. The droplets had a set size with the tail end slowly fading away. The droplets were also falling at different speeds. I focused on these characteristics of the droplet.

I kept it very simple at the beginning by creating a simple algorithm in my main.cpp file. This algorithm seen below creates a vector of characters and prints them out 1 by 1 on the screen, when it prints the whole vector it starts "removing" (just placing an empty character) at the tail end of the vector seen on the screen, it then goes to back to the beginning of the vector and starts printing the characters again.
It's a very simple algorithm and I based the whole project on that simple idea.

*note: the GoToXY() function simply goes to a position on the screen given the X and Y coordinate*

<img src="https://raw.githubusercontent.com/PatMilk96/DigitalRainBlog/main/docs/assets/images/OriginalAlgorithm.jpg" width="650" height="400">
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
The key functions here are the *GoToXY()* which allows me to go to a certain X and Y coordinate on the screen to print a character in that exact position *SetSpeed()* function finds how many objects are being initialized for the current window size and sets the appropriate speed, *GenerateRandomChars()* that uses a rand() function to generate a vector of random characters, *ReturnRand()* that I can call to return two integers so I can set a different random speed to a droplet once it has reached the end, *BottomReachedFunction()* that that starts removing characters from the tail end of the droplet and once all are removed it populates the vector with new characters, *Init()* that removes the cursor and then populates a vector of objects with my Rain droplets, finally we have the *Print()* function that prints out the vectors of characters from my droplets.


**DigitalRain.h**

In this file, I provide all my public function definitions and private variables

<img src="https://raw.githubusercontent.com/PatMilk96/DigitalRainBlog/main/docs/assets/images/Header.png" width="650" height="600">
[img 1.2]

In my *private* section I define all the variables that my object holds. These are the vector of characters, a vector of speeds, my *arrP* that holds a value that represents the character position within the *chars* vector, 'x' and 'y' which are the coordinates for the *GoToXY() function, *speed* which is the current speed of the droplet (this is how many times I will "skip" the print function), and *vectorPos* which is just the position of my object within the vector of objects created in *main.cpp* 


## Design And Implementation

In the main.cpp file I initialize my Rain object (Rain rain;) that holds all the attributes for my droplet, then I initialize a vector of rain objects called raindrops (std::vector<Rain> raindrops;), creating my droplets. After that, I have an infinite loop that iterates through my raindrops and prints them on the screen.

<img src="https://raw.githubusercontent.com/PatMilk96/DigitalRainBlog/main/docs/assets/images/main.png" width="650" height="600">
[img 1.3]

Let's move to the *Init()* function:

<img src="https://raw.githubusercontent.com/PatMilk96/DigitalRainBlog/main/docs/assets/images/Init.png" width="650" height="600">
[img 1.4]

The main purpose of this function is to remove the cursor, get the screen size, and populate the raindrops variables. The raindrops are placed in a random 'y' position on the screen for a nice effect. After this is done, the function is never called again and the *Print()* function does most of the work here.

<img src="https://raw.githubusercontent.com/PatMilk96/DigitalRainBlog/main/docs/assets/images/Print.png" width="650" height="600">
[img 1.5]

The *Print()* function follows the same pattern as the *OriginalAlgorith*

the first *if* statement checks if all characters have been printed, and if they have then it sets the vector position back to the start of the vector.

Then we have the main *if* *else* statement. First I check if the Y position is not the same as the bottom of the screen, if it is then I check the speed. If the speed is equal to zero then I can call my *BottomReached()* function [img 1.6] and start removing the tail end of the droplet by printing an empty character in its place and using pop to remove the characters from the vector and if they're all removed I populate the vector with random characters, if it's not zero then decrement it and move to the next droplet. After the *BottomReached()* function is called I set the speed back to the original speed. Then I check if the size is 1 and if it is then I set a random speed and place it in the *SpeedsCopy* vector. The *ReturnRand* function is used here [img 1.7]. This function was created with the help of ChatGPT.  It is a calculation that returns two random values based on the amount of objects on the screen. The amount of object is the same as half the size of the screen. ChatGPT was given the numbers for the biggest screen The max value is x = 156  (y=150 : z=50) and min screen x = 6 (y=1500 : z=1000) and was asked to provide a calculation for 'y' and 'z' given the input 'x' while satisfying the min and max values.


Going back to the beginning of the function where I check if the Y position is not the same as the bottom of the screen (height). When it's not, then I can continue to print the characters. It's that classic upgraded *OriginalAlgorith* here... Go to X, Y, print a character, remove the tail end, increment the Y, increment the vector of characters position, and reset the speed. If the speed is greater than 0 then decrement it.


<img src="https://raw.githubusercontent.com/PatMilk96/DigitalRainBlog/main/docs/assets/images/BottomReached.png" width="650" height="600">
[img 1.6]


<img src="https://raw.githubusercontent.com/PatMilk96/DigitalRainBlog/main/docs/assets/images/ReturnRand.png" width="650" height="600">
[img 1.7]

## Conclusion

Overall the project came out very well. I managed to recreate the original digital rain from 'The Matrix'. I was initially planning to use Japanese characters just like in the movie, but my priority was to get the basic functionality working. I did try to Implement the Japanese characters but that proved to be more difficult and I decided not to spend my time on it and focused on other aspects, such as the screen re-size option. The screen re-size option could have been implemented better as the screen size can only be adjusted once at the beginning, and any other adjustments after that will break the simulation and continuously checking the screen size caused the simulation to lag and lose its look. I tried to keep my code simple but as I went along and added more features and tried to get closer to the movie look it got progressively more and more complex. I plan to work some more on the code in the future and add some additional features that I didn't have time to add, like the Japanese characters and maybe some sushi recipes. I'd also like to add a fade away effect to the end of my droplets to give it an even better look. One last feature I hope to implement is adding a new object in the same Y coordinate when there is sufficient space, currently I have a fixed number of object and keep printing them in the same line with different speeds and sizes.

#References

[Console Window Size](https://learn.microsoft.com/en-us/archive/msdn-technet-forums/0de248af-3497-4537-bb41-6d129b04fb27).


