---
layout: post
title: Why is the meaningless () used in Python?
date: 2023-09-27 20:10:20 +0900
description: # Add post description (optional)
img: parathesese.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Python, Why?]
---

Last night, it took me four hours to find just one error while working on my assignment. The reason? It was solely because of these "()" parentheses. Many Python programmers use empty "()" quite frequently, and I couldn't help but feel an inexplicable sense of betrayal as I realized I had wasted my time over this tiny detail. So, today, I'm going to write about why this little thing is necessary.

In Python, empty parentheses `()` have a specific purpose and are not meaningless. They are used to create instances of classes, including built-in classes and user-defined classes. The empty parentheses indicate the instantiation of an object, invoking the class constructor (the `__init__` method) without passing any arguments.

Here's why empty parentheses are used in Python:

1. **Class Instantiation**: When you create an instance of a class, you use empty parentheses to call the class constructor. For example:

   ```python
   class MyClass:
       def __init__(self):
           print("An instance of MyClass has been created.")

   obj = MyClass()  # Instantiating MyClass using empty parentheses
   ```

   In this example, `MyClass()` creates an instance of the `MyClass` class.

2. **Default Constructors**: If a class doesn't define its own `__init__` method, Python provides a default constructor that takes no arguments. In this case, empty parentheses are still used for instantiation.

   ```python
   class DefaultClass:
       pass

   obj = DefaultClass()  # Instantiating DefaultClass using empty parentheses
   ```

3. **Invoking Methods**: Parentheses are also used to invoke methods on objects. When you call a method on an object, you use parentheses to pass any required arguments to the method.

   ```python
   class MyClass:
       def say_hello(self):
           print("Hello, world!")

   obj = MyClass()
   obj.say_hello()  # Invoking the say_hello method with ()
   ```

   Here, `say_hello()` is a method call on the `obj` object.

4. **Function Calls**: Outside the context of classes, parentheses are used for calling functions. Functions are callable objects, and you use `()` to provide arguments and call them.

   ```python
   def greet(name):
       print(f"Hello, {name}!")

   greet("Alice")  # Calling the greet function with ()
   ```

In summary, empty parentheses `()` are not meaningless in Python. They are an essential part of the language syntax used for creating instances of classes, invoking methods, and calling functions. They serve as a way to pass arguments when necessary, even if no arguments are required, as in the case of class instantiation or calling functions with no parameters.

After doing some research, it seems like I may have been wrong in my initial statement. I must make sure never to make such a mistake again in the future.