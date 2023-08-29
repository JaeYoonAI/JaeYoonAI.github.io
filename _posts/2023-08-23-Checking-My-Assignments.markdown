---
layout: post
title: 2023-08-23-TIL 2 Python Projects retrospective
date: 2023-08-23 19:30:20 +0900
description: Up&Down Rock-Scissors-Paper # Add post description (optional)
img: rsp.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Up&Down, Python, Rock-Scissors-Paper]
---

I'm going to compare what I did yesterday with what I edited while listening to the commentary lecture today.

<h1>Up & Down</h1>

```python
import random

random_number = random.randint(1, 100)

count = 1

while True:
    x = int(input('Choose Your Number: '))
    if x < random_number:
        count += 1
        print('Up')
    elif x > random_number:
        count += 1
        print('Down')
    if x == random_number:
        print('You make it! the number is %d and you try %dtimes.' % (x, count))
        break

```
Below is the code I edited.

```python
import random

max_try = 0

while True:
    random_number = random.randint(1, 100)
    print(f'Your highst try number is {max_try}')

    count = 0

    # I add 'count += 1' on if and elif but change to outside of if and elif so the count start with '0'

    while True:
        x = int(input('Choose Your Number(1~100): '))
        if x > 100 or x < 1:
            print('Please enter the number between 1-100')
            continue
        count += 1
        if x < random_number:
            print('Up')
        elif x > random_number:
            print('Down')
        if x == random_number:
            print(
                f'You make it! the number is {random_number} and you try {count}times.')
            if count > max_try:
                max_try = count
            break

    will_continue = input('continue?(y/n): ')
    if will_continue == 'y':
        continue
    if will_continue == 'n':
        break
```
There was no problem with what I did before. However, I couldn't add additional features, but I added them while listening to the commentary.  

First, 'count' started from the inside of 'while' and started from 1, but I set it to count before coming out of 'while' and 'input'.  
Then, I made a selection with 'input' so that I could play the game continuously, and then I made it possible to run 'while' again.  
And I made it print the maximum number of attempts.
<h1>Rock-Scissors-Paper</h1>

```python
import random

rsp = ['Rock', 'Scissors', 'Paper']

a = input(
    'This is Rock Scissors Paper Game. Do you want to play the game or not? (Y/N): ').lower()

w = 0
l = 0
d = 0

if a == 'y':
    while True:
        computer = random.choice(rsp).lower()
        x = input('Choose one (Rock, Scissors, Paper): ').lower()
        while computer == 'rock':
            if x == 'scissors':
                print('Lose.')
                l += 1
            if x == 'paper':
                print('Win')
                w += 1
            if x == computer:
                print('Draw.')
                d += 1
            else:
                print('Wrong Input')
            break
        while computer == 'paper':
            if x == 'scissors':
                print('Win.')
                w += 1
            if x == 'rock':
                print('Lose.')
                l += 1
            if x == computer:
                print('Draw.')
                d += 1
            else:
                print('Wrong Input')
            break
        while computer == 'scissors':
            if x == 'paper':
                print('Lose.')
                l += 1
            if x == 'rock':
                print('Win.')
                w += 1
            if x == computer:
                print('Draw.')
                d += 1
            else:
                print('Wrong Input')
            break
        a = input(
            'Continue? (Y/N): ').lower()
        if a == 'y':
            continue
        if a == 'n':
            break


if a == 'n':
    print('Game Over')
    print('Win: %d, Lose: %d, Draw: %d' % (w, l, d))

```
Below is the code I edited.

```python
import random

rsp = ['rock', 'scissors', 'paper']

a = input(
    'This is Rock Scissors Paper Game. Do you want to play the game or not? (Y/N): ').lower()

w = 0
l = 0
d = 0

if a == 'y':
    while True:
        computer = random.choice(rsp).lower()
        x = input(
            'Choose one (Rock, Scissors, Paper) or quit the game?(q): ').lower()
        if x == 'q':
            break
        # inserting q position is important!
        if x not in rsp:
            print('Wrong Input')
            continue
        while computer == 'rock':
            if x == 'scissors':
                print('Lose.')
                l += 1
            if x == 'paper':
                print('Win')
                w += 1
            if x == computer:
                print('Draw.')
                d += 1
            break
        while computer == 'paper':
            if x == 'scissors':
                print('Win.')
                w += 1
            if x == 'rock':
                print('Lose.')
                l += 1
            if x == computer:
                print('Draw.')
                d += 1
            break
        while computer == 'scissors':
            if x == 'paper':
                print('Lose.')
                l += 1
            if x == 'rock':
                print('Win.')
                w += 1
            if x == computer:
                print('Draw.')
                d += 1
            break


print('Game Over')
print(f'Win: {w}, Lose: {l}, Draw: {d}')
```
Regarding limiting the user's input value to 'rock paper scissors', I tried to use 'else' in each 'while', but 'Wrong Input' is output even if the correct value is entered.  

I solve this problem by using 'if A not in B'.  
I tried to set an exception in each phrase according to the computer's choice, but surprisingly the correct answer was solved in one line outside.



And I had to receive an 'input' about whether to continue or end the game, but in the first version it seemed cumbersome, so I combined it with a sentence to select rock paper scissors.  
The location of the 'break' for this was very important.

Doing these two things gave me a little bit of confidence.   
Looking forward to learning more in the future.

While thinking about the importance of the location of the 'break', I felt deeply what it meant to say that coding is the same as the order in which people think, and that in the end it should be easily read by people.

