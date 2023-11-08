---
layout: post
title: Environment Variables in Python
date: 2023-11-08 20:10:20 +0900
description: Environment Variables in Python  # Add post description (optional)
img: logo-python.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Python, Environment Variables]
use_math: true
---

I've been preparing for technical interviews little by little while working on my last project. Today, I came across a few questions, and one of them was about environment variables. Besides the initial Python installation, it was a topic I hadn't thought about at all. It can be a bit tricky to grasp, so I'm writing it down in my post.

Setting environment variables in Python can be useful for various reasons, such as storing sensitive information, configuring application behavior, or customizing runtime settings. Here's why and how to set environment variables in Python:

# Why Set Environment Variables in Python: #

1. **Configuration Management**: Environment variables are commonly used to manage configuration data that may change between different environments (e.g., development, testing, production). Storing configuration data separately from the code allows for easy customization without modifying the source code.

2. **Security**: Sensitive information, like API keys, database credentials, or authentication tokens, can be stored as environment variables. This enhances security by preventing the exposure of sensitive data in source code or configuration files.

3. **Behavior Control**: Environment variables can influence the behavior of your Python application. For instance, you might use an environment variable to toggle between development and production modes or control feature flags.

4. **Compatibility**: Environment variables make your code more portable, as you can change application behavior without altering the codebase. This is especially important when deploying software to different environments or platforms.

# How to Set Environment Variables in Python: #

1. **Using the `os` Module**: Python provides the `os` module to interact with environment variables.

   - To set an environment variable, use `os.environ["VARIABLE_NAME"] = "VALUE"`. For example:
     ```python
     import os
     os.environ["API_KEY"] = "your_api_key_here"
     ```

   - To access an environment variable, use `os.environ["VARIABLE_NAME"]`. For example:
     ```python
     import os
     api_key = os.environ["API_KEY"]
     ```

2. **Setting Environment Variables in the Shell**:

   - You can set environment variables outside of your Python code, typically in the command line or shell, before running your Python script. The exact command may vary depending on your operating system.

     - In Windows, you can use the `set` command:
       ```
       set API_KEY=your_api_key_here
       python your_script.py
       ```

     - In Unix-based systems (Linux, macOS), you can use `export`:
       ```
       export API_KEY=your_api_key_here
       python your_script.py
       ```

3. **Using `.env` Files**: For local development or when using tools like Python's `python-dotenv`, you can store environment variables in a `.env` file and load them into your Python application using libraries. This is a common practice in web development and simplifies configuration management.

   - Sample `.env` file:
     ```
     API_KEY=your_api_key_here
     DEBUG=True
     ```

   - In Python, use a library like `python-dotenv` to load `.env` files:
     ```python
     from dotenv import load_dotenv
     load_dotenv()
     api_key = os.environ["API_KEY"]
     ```

Remember that environment variables set within a Python script or a shell session are only available within that context. To persist environment variables across system reboots or make them accessible to other processes, you'll need to configure system-level environment variables using your operating system's settings or scripts.