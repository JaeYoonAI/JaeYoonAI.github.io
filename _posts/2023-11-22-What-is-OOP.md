---
layout: post
title: What is OOP(Object-Oriented Programming)
date: 2023-11-22 20:10:20 +0900
description: What is OOP(Object-Oriented Programming)  # Add post description (optional)
img: logo-python.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Python, OOP]
use_math: true
---

Object-Oriented Programming (OOP) is a programming paradigm that uses the concept of "objects" to organize code. It revolves around the idea of bundling data and the methods that operate on the data into a single unit, known as an object. These objects can be instances of classes, which serve as blueprints for creating objects.

### Core Concepts of OOP:

1. **Class:** A class is a blueprint or template for creating objects. It defines the attributes (data) and methods (functions) that the objects will have.

2. **Object:** An object is an instance of a class. It represents a concrete occurrence based on the blueprint defined by the class.

3. **Encapsulation:** Encapsulation is the bundling of data and methods that operate on the data into a single unit (class). It hides the internal details of how an object works.

4. **Inheritance:** Inheritance allows a new class (subclass/derived class) to inherit attributes and methods from an existing class (base class/parent class). It promotes code reuse and establishes a relationship between classes.

5. **Polymorphism:** Polymorphism allows objects of different classes to be treated as objects of a common base class. It enables the same method or operation to behave differently based on the context.

### Example:

Let's consider an example of a simple `Car` class in Python:

```python
class Car:
    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year
        self.speed = 0

    def accelerate(self):
        self.speed += 5
        print(f"The car is accelerating. Current speed: {self.speed} mph")

    def brake(self):
        if self.speed >= 5:
            self.speed -= 5
            print(f"The car is braking. Current speed: {self.speed} mph")
        else:
            print("The car is already stopped.")

# Creating instances (objects) of the Car class
car1 = Car("Toyota", "Camry", 2022)
car2 = Car("Ford", "Mustang", 2023)

# Using methods of the Car class
car1.accelerate()
car2.accelerate()
car1.brake()
car2.brake()
```

In this example:
- We have a `Car` class with attributes (make, model, year, speed) and methods (accelerate, brake).
- `car1` and `car2` are instances of the `Car` class.
- We use the methods to perform actions on the cars, such as accelerating and braking.

This example demonstrates encapsulation, as the data (make, model, year, speed) and methods are bundled together in the `Car` class. The `accelerate` and `brake` methods represent the behavior of a car, and multiple instances of the `Car` class (objects) can be created and manipulated independently. Inheritance and polymorphism are not explicitly used in this example but could be applied to extend the functionality of the `Car` class or create specialized types of cars.