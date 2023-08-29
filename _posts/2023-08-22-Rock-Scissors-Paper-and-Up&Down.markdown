---
layout: post
title: 2023-08-22-TIL 2 Python Projects
date: 2023-08-22 19:30:20 +0900
description: Up&Down Rock-Scissors-Paper # Add post description (optional)
img: rsp.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Project, Python, Rock-Scissors-Paper]
---
I was given three assignments, but I finished the easiest two first.


Below is the code I wrote.
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

Import the random received as a hint and randomly select numbers from 1 to 100.  
And I used 'while' to keep it running.
'if' and 'elif' for distinguish the number.
'count +=1' for showing the number of try.
'%d' for print the counting number.

The first problem was solved simpler than expected.

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

It was so hard for me actually.  
And I was very doubtful that I would be able to do this.  

At first, it took a long time to think about how it was possible while using only one 'while'.  
When I looked up about using 'while', I realized that it could be used overlapping, so I applied it right away.  
Regarding limiting the user's input value to 'rock paper scissors', I tried to use 'else' in each 'while', but 'Wrong Input' is output even if the correct value is entered.  

As soon as this issue is resolved, I will write about it in the next post.


Doing these two things gave me a little bit of confidence.   
Looking forward to learning more in the future.


