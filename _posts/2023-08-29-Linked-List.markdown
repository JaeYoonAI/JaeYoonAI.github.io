---
layout: post
title: Linked List
date: 2023-08-28 20:30:20 +0900
description: Find the Palindrome # Add post description (optional)
img: algo.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Find the Palindrome, Python, Algorithm]
---

Today I'm going to talk about 'Linked List'.  
The concept itself is not difficult to understand, as the picture below shows.

<img src="/assets/img/linked.png" width="620" height="314">

The 'linked list' is cumbersome to find, but it is a very good way to add and delete contents.

I'm trying to write in the direction I understand.


```python
# First create the first room with nothing in it.
class LinkedList:
    def __init__(self):
        self.head = None
# And declare a function to 'append' the other rooms.
    def append(self, val):
        # If there is no head at the first start
        if not self.head:
            self.head = ListNode(val, None)
            return
        # If the head already exists, it will continue to the next room, find the one without 'next' and 'append' to it.
        node = self.head
        while node.next:
            node = node.next

        node.next = ListNode(val, None)

# Now we convert a normal list to a 'Linked List'.
lst = [1, 2, 3]
l1 = LinkedList()
for e in lst:
    l1.append(e)
print(l1)
```

With this level of understanding, I took the quiz right away.

<h1>Palindrome Linked List
</h1>

- Given the ```head``` of a singly linked list, return ```true``` if it is a palindrome(A palindrome is a sequence that reads the same forward and backward.) or ```false``` otherwise.
- Example 1 &nbsp;&nbsp;Input: head = [1,2,2,1]  
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Output: true
- Example 2 &nbsp;&nbsp;Input: head = [1,2]  
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Output: false

```python
# Imported the same thing as 'append' to 'linked list'.
class LinkedList:
    def __init__(self):
        self.head = None
    def append(self, val):
        if not self.head:
            self.head = ListNode(val, None)
            return
        node = self.head
        while node.next:
            node = node.next

        node.next = ListNode(val, None)

# Declare a function called 'isPalindrome'.
def isPalindrome(head):
    arr = []
    # 'True' if the first room is empty
    if not head:
        return True
    # Append 'head', which is made in the form of 'linked list', into 'list' called 'arr'.
    node = head
    while node:
        arr.append(node.val)
        node = node.next
    # It compares the first and last number using 'pop' and returns 'False' if they are not equal.
    while len(arr) > 1:
        if arr.pop(0) != arr.pop():
            return False

    return True

l1 = LinkedList()
for num in [1, 2, 2, 1]:
    l1.append(num)

l2 = LinkedList()
for num in [1, 2]:
    l2.append(num)

print(isPalindrome(l1.head))
print(isPalindrome(l2.head))
```

Even now, I don't really understand much.  
But I will continue to challenge myself without giving up.