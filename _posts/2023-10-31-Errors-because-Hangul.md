---
layout: post
title: unicodedecodeerror 'utf-8' codec can't decode byte 0xb4 in position 29 invalid start byte because of "한글"
date: 2023-10-31 20:10:20 +0900
description: Errors that occur because it is Hangul # Add post description (optional)
img: hangul.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Python, ML]
use_math: true
---


Today, during a machine learning lecture, there was a significant time thief that disrupted my progress. It was the error message 

```unicodedecodeerror: 'utf-8' codec can't decode byte 0xb4 in position 29: invalid start byte. ```

Although I searched for solutions within the lecture's Q&A, only TensorFlow and NumPy version issues were mentioned. I even reinstalled Anaconda3 and tried changing versions, but in the end, I found the solution through a Google search.

The error was caused by the presence of Korean characters in the project folder's path. When I moved my project to the root folder of the C drive, it started working perfectly. I guess I'll have to remove all Korean characters from my computer setup in the future.