---
layout: post
title: 2023-08-17-TIL Python Naming Convention and install on VScode
date: 2023-08-17 20:16:20 +0900
description: Python Naming Convention # Add post description (optional)
img: pythonpep8.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Developer, Python, PEP8]
---

Like all languages, computer languages ​​have grammar.

Python have own grammar also.

And each developer have own style.

Code Convention is a "promise" to unify the style to avoid confusion.

Python provides a convention guide called PEP-8.

Below is the content of the naming convention.

# 1. General
* Avoid using names that are too general or too wordy. Strike a good balance between the two.
* Bad: data_structure, my_list, info_map, dictionary_for_the_purpose_of_storing_data_representing_word_definitions
* Good: user_profile, menu_options, word_definitions
* Don’t be a jackass and name things “O”, “l”, or “I”
* When using CamelCase names, capitalize all letters of an abbreviation (e.g. HTTPServer)
# 2. Packages
* Package names should be all lower case
* When multiple words are needed, an underscore should separate them
* It is usually preferable to stick to 1 word names
# 3. Modules
* Module names should be all lower case
* When multiple words are needed, an underscore should separate them
* It is usually preferable to stick to 1 word names
# 4. Classes
* Class names should follow the UpperCaseCamelCase convention
* Python’s built-in classes, however are typically lowercase words
* Exception classes should end in “Error”
# 5. Global (module-level) Variables
* Global variables should be all lowercase
* Words in a global variable name should be separated by an underscore
# 6. Instance Variables
* Instance variable names should be all lower case
* Words in an instance variable name should be separated by an underscore
* Non-public instance variables should begin with a single underscore
* If an instance name needs to be mangled, two underscores may begin its name
# 7. Methods
* Method names should be all lower case
* Words in an method name should be separated by an underscore
* Non-public method should begin with a single underscore
* If a method name needs to be mangled, two underscores may begin its name
# 8. Method Arguments
* Instance methods should have their first argument named ‘self’.
* Class methods should have their first argument named ‘cls’
# 9. Functions
* Function names should be all lower case
* Words in a function name should be separated by an underscore
# 10.  Constants
* Constant names must be fully capitalized
* Words in a constant name should be separated by an underscore

This is jsut a summary of the naming convention, but there is a lot of information when you enter the PEP8 site.

At the VScode Extention. find Autopep8 and install.
At the Settings you can find open setting(JSON) on upper right side.

Please type below code and save.

Every time you save a file, it automatically changes to match the syntax.



```python
{
    "terminal.integrated.defaultProfile.windows": "Git Bash",
    "[python]": {
        "editor.defaultFormatter": "ms-python.autopep8",
        "editor.formatOnSave": true
    }
}
```
If you don't want to automatically changeing.

Just replace true to false.

and you can fix your style just press [ alt + shift + f ]
