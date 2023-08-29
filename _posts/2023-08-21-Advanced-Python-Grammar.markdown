---
layout: post
title: 2023-08-21-TIL Finishing Advanced Python Grammar
date: 2023-08-21 20:00:20 +0900
description: Class and Decorator # Add post description (optional)
img: logo-python.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Decorator, Python, Class]
---


It was not a lot of lecture, but I finally finished the python intensive course.

Below are a few things I would like to check again.

<h1>Class
</h1>

1. \__init__
   * If \__init__ method is used in class, the corresponding method will run when an instance is created.
     * ```python
        class CookieFrame():
        def __init__(self, name):
        print(f"The name of the created cookie is {name}")
        self.name = name

        cookie1 = CookieFrame("cookie1") # The name of the created cookie is cokkie1
        cookie2 = CookieFrame("cookie2") # The name of the created cookie is cokkie2
        ```
2. inheriting
   * Class inheritance in python is a function that allows you to import and use features such as variables and methods declared in other classes when creating a class.
   * At this time, the inheriting class is called parents or super class, and inherited class is called child or sub class.
     * ```python
        class Monster():
            def __init__(self, hp):
                self.hp = hp
                
            def attack(self, damage):
                self.hp -= damage

            def status_check(self):
                print(f"monster's hp : {self.hp}")
                
        class FireMonster(Monster):
            def __init__(self, hp):
                self.attribute = "fire"
                # super() allows you to use the parent class's code as-is.
                # The code is the same as executing code self.hp = hp.
                super().__init__(hp)
            
            # Override the status_check method that exists in the parent class.
            def status_check(self):
                print(f"fire monster's hp : {self.hp}")
                
        class IceMonster(Monster):
            def __init__(self, hp):
                self.attribute = "ice"
                super().__init__(hp)
            
            def status_check(self):
                print(f"ice monster's hp : {self.hp}")
                
        fire_monster = FireMonster(hp=100)
        fire_monster.attack(20)
        fire_monster.status_check()

        ice_monster = IceMonster(hp=200)
        ice_monster.attack(50)
        ice_monster.status_check()
        ```
   * Always use child classes to avoid errors when using classes already created by others.
  
  <h1>Decorator
</h1>

  1. Description
      * Decorators are written in the form of @decorator using '@' on top of the declared function, and when the function is executed, the code declared in the decorator is executed as well.
  2. Example
     * ```python
        # Finding the Execution Time of a Specific Function
        import time
        import random

        def time_checker(func):
            def wrapper():
                # Stores the time when the function runs.
                start_time = time.time()

                # Running the function
                func()

                # When the function runs at the hour after it exits, subtract the time to get the running time.
                executed_time = time.time() - start_time

                # Outputs the execution time to 5 decimal places only.
                print(f"{func.__name__} function execution time : {executed_time:.05f}s")

            return wrapper

        @time_checker
        def main():
            time.sleep(random.randint(1, 10) / 10)

        for i in range(10):
            main()

        # result output
        """
        main function execution time : 0.80095s
        main function execution time : 0.90009s
        main function execution time : 1.00027s
        main function execution time : 0.20020s
        main function execution time : 0.90011s
        main function execution time : 0.60041s
        main function execution time : 0.30027s
        main function execution time : 0.40024s
        main function execution time : 0.10026s
        main function execution time : 0.50032s
        """
        ```
      * In addition, you can create a function by inserting an argument into it, so if you use this decorator, you can create an infinite number of functions.  


I haven't started the personal assignment I mentioned last time, but I finished the class today and can proceed properly from tomorrow.
