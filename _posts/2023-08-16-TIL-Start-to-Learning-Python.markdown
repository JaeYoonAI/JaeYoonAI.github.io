---
layout: post
title: 2023-08-16-TIL
date: 2023-08-16 20:36:20 +0900
description: Start to Learning Python # Add post description (optional)
img: pycharm.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Developer, Python, Pycharm]
---

After finishing the web development class, I started learning Python.

I had gone through the Python handbook 3 weeks ago, so the first part was easy to follow.

The hardest thing I learned today was counting numbers and adding numbers in a list.

* Print the number of even numbers in a list

```python
num_list = [1, 2, 3, 6, 3, 2, 4, 5, 6, 2, 4]

count = 0

for num in num_list:
    if num % 2 == 0:
        count += 1

print(count)
```

* Add all the numbers in the list

```python
num_list = [1, 2, 3, 6, 3, 2, 4, 5, 6, 2, 4]

result = 0
for num in num_list:
    result += num

print(result)
```


I didn't understand the meaning of '+=' at first, but as I worked through some examples, it got stuck in my head.