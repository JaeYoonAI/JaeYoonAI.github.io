---
layout: post
title: 2023-08-18-TIL Starting My First Personal Project Using Python
date: 2023-08-18 20:16:20 +0900
description: 3 little games using python # Add post description (optional)
img:  logo-python.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Developer, Python, game]
---

I still lack a lot of knowledge about Python, but I'm going to start 3 simple projects.

Brief details of these 3 projects are as follows.

# 1. Up & Down Game (Korean Drinking Game)
* Create up & down games involving players and computers.
* Programs must include the following features:
  * A computer generates a random number between 1 and 100.
  * The player inputs a number and compares the number entered with the number on the computer to give an "up" or "down" hint.
  * If the player guesses the number on the computer correctly, it tells the number of attempts.
  * Repeat the above process until the player guesses the number.
* About random module
    *   ```python
        import random

        random_number = random.randint(1, 100)
        ```  

# 2. Rock Paper Scissors Game
* Create a rock-paper-scissors game involving players and the computer.
* The game is played in the following order.
  * The player enters one of scissors, rock, or paper.
  * The computer also randomly chooses between scissors, rock, and paper.
  * The player's and computer's choices are compared to determine a win or loss.
  * Print the result to tell if the player won, the computer won, or a tie.
  * Add the ability to repeat or quit the game.



# 3. Simple Social Media Platform
* In this project, I will develop a program to manage members and posts on a simple social media platform.
* Define a ```Member``` class and a ```Post``` class.
* The ```Member``` class should have the following properties:
  * Member name (```name```)
  * Member ID (```username```)
  * Member password (```password```)
* The ```Member``` class should have the following methods.
  * A ```display``` that prints member information (password must not be shown!)
* The ```Post``` class must have the following properties.
  * Posting title (```title```)
  * Posting content (```content```)
  * Author (```author```): Member's ```username``` must be saved!
* Create at least 3 member instances and save them using append to an empty list called ```members```.
  * Cycle through the members list and print all member names
* Please create a code that allows each member to post three or more posts (a total of 9 or more post instances must be created for three members). Save the created post instances using append to the posts empty list.
  * Print all titles of posts written by a specific user using "for"
  * Print all the titles of posts that contain ‘specific words’ in the content using "for"


I have to complete all of the above in 5 days including the weekend.  

I haven't finished the Python advanced course, so I'm going to finish this first and then start.

I learned various grammars of Python today, but there is a part that I was worried about while learning.

It is a part that judges 'true' and 'false' while using 'if'.

I felt it was a grammar that would go into any project, and I found out that it could be used in a variety of ways.


I will write more about details of grammar in another post.