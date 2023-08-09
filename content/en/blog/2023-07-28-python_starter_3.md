---
title: When a R user began coding with Python III
date: 2023-07-28T16:00:21-04:00
author: Xinting Du
slug: bookdown-tips
draft: false
toc: true
tags: Python
---



In this document, we continue our study on basics of Python.



## Method

In Python, a method is a function that is associated with an object.
It only works with that object
It is used with dot notation: object.method()

Check more list methods [here](https://www.w3schools.com/python/python_ref_list.asp)
String methods [here](https://www.w3schools.com/python/python_ref_string.asp)



```python

cars = ['Ford', 'BMW']
cars.append('Mazda')
print(cars)

cars.sort()
print(cars)

```

## Function

In Python, a function is a named block of code that performs a specific task or set of operations. 

Functions are **reusable** blocks of code that allow you to break down a larger problem into smaller, manageable parts.


```python

def is_even(i):
    """
    Input: i, a positive integer
    Returns True if i is even, otherwise False
    """
    return i % 2 == 0
is_even(5)


## def is the keyword used to define the function

## name of the function comes after def， in this case is_even is the name
## then, in (), comes the parameters / arguments, in this case, **i** is the only argument
## return something
```

## Module

In Python, a module is a file containing Python definitions and statements. The module allows you to organize your code logically and separates it into reusable components.
To use a module in Python, we need to import the module.


```python

## import the entire module and access its contents using dot notation
import math
print(math.sqrt(16))  # Output: 4.0

## import specific functions or variables from the module
from math import sqrt
print(sqrt(16))  # Output: 4.0

## import the module and rename it
import numpy as np

## import specific function and rename it
from math_operations import subtract as sub

```












