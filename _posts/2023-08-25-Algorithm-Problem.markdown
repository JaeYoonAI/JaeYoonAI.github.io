---
layout: post
title: Algorithm Problems
date: 2023-08-25 20:30:20 +0900
description: Up&Down Rock-Scissors-Paper # Add post description (optional)
img: logo-python.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Class, Python, Algorithm]
---

Algorithm problem solving started yesterday, and classes on it began.

Solving the problem is going on for an hour every day, but I spent quite a bit of time holding on to the unsolved problem.

There are a lot of problems for each level provided by the site called 'Programmers'.  
And when it is linked with 'git hub' and the answer to the problem is correct, it is stored in my repository.   
For details on how to link, search 'backjoonhub'.


I have only solved 4 problems so far, but I would like to introduce one of them.

<h1>Sum of Divisors</h1>

-  Complete a function, ```solution```, that receives an integer ```n``` and returns the sum of all divisors of ```n```.

```python
def solution(n):
    answer = 0
    a = int(n)
    if a <= 3000:
        for i in range(1, a+1):
            if a % i == 0:
                answer = answer + a/i
    return int(answer)


print(solution(16)) #31
#Right answer
```
It looks very simple, but it took me about an hour to solve this problem.  
There are so many ways to make coding easier, but trying to start from nothing was so difficult at first.  
The reason why it took the longest time was that when I first wrote 'range', I only wrote 'a' instead of 'a+1'.  
So all the results came out short of 1.
```python
def solution(n):
    answer = 0
    a = int(n)
    if a <= 3000:
        for i in range(1, a):
            if a % i == 0:
                answer = answer + a/i
    return int(answer)


print(solution(16)) #30
#Wrong answer
```
So I thought that something was wrong and I should have started with 'answer = 1', but mysteriously it did not pass on the 'Programmers' site.  
After thinking about it for a long time, I finally saw the code written by other people and realized that everyone put +1 at the end of 'range'.  
I finally realized When setting the range, 'range(a, b)' does not include 'b'.


I learned it when I first learned the Python language, but I had already forgotten it.

Please be careful 'range'