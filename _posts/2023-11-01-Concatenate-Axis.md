---
layout: post
title:  numpy.concatenate in detail, including its axis
date: 2023-11-01 20:10:20 +0900
description: numpy.concatenate function # Add post description (optional)
img: image8.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Python, ML]
use_math: true
---

When processing images and rejoining them after some operations, there are cases where you need to use the `numpy` `concatenate` function with different settings for the `axis`. Today, I intend to write about this.


`numpy.concatenate` is a function used in NumPy to combine (concatenate) arrays. This function allows you to specify the axis along which you want to concatenate arrays. The `axis` parameter is an integer that indicates the axis of the arrays to be concatenated. Here are some examples to illustrate the usage of the `numpy.concatenate` function:

First, let's create two NumPy arrays as follows:

```python
import numpy as np

arr1 = np.array([[1, 2], [3, 4]])
arr2 = np.array([[5, 6]])
```

1. **Basic Concatenation (axis=0)**:
   - When you use `axis=0`, the arrays are concatenated along the vertical direction.

```python
result = np.concatenate((arr1, arr2), axis=0)
print(result)
```

Result:

```
[[1 2]
 [3 4]
 [5 6]]
```

2. **Concatenation with axis=1 (Horizontal)**:
   - Using `axis=1`, the arrays are concatenated horizontally.

```python
result = np.concatenate((arr1, arr2.T), axis=1)  # Transpose arr2 to concatenate horizontally
print(result)
```

Result:

```
[[1 2 5]
 [3 4 6]]
```

3. **Concatenating Multiple Arrays**:
   - You can concatenate multiple arrays.

```python
arr3 = np.array([[7, 8]])
result = np.concatenate((arr1, arr2, arr3), axis=0)
print(result)
```

Result:

```
[[1 2]
 [3 4]
 [5 6]
 [7 8]]
```

4. **Concatenation without specifying `axis`**:
   - If you don't specify the `axis` parameter, it defaults to `axis=0`.

```python
result = np.concatenate((arr1, arr2))  # Axis is not specified (default is axis=0)
print(result)
```

The result is the same as in the first example.

By using the `numpy.concatenate` function with the appropriate `axis` parameter, you can concatenate arrays in the desired direction.