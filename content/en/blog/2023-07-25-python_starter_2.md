---
title: When a R user began coding with Python II
date: 2023-07-25T16:00:21-04:00
author: Xinting Du
slug: bookdown-tips
draft: false
toc: true
tags: Python
---


1. Recap

In [When a R user began coding with Python I](), we learn about: 
- the IDEs, 
- mathematical operations, 
- basic data types, 
- variables, 
- branching, and iteration
- comparison and logical operators

2. This document

In this document, we push forward the learning process and focus on three data structures used to store and organize data: list, dictionary, and tuple.


## List:

A list is an **ordered collection of items**, and it can contain elements of different data types. 
Lists are **mutable**, which means you can modify their contents after they are created. 
Lists are defined using square brackets \[\], and elements are separated by commas. 
An item in the list can occur more than once.
Elements could be accessed in a list using their index, and can be performed various operations like appending, removing, slicing, etc.


```python

my_list = ['apple', 'orange', 'banana', 'cherry']
type(my_list)
my_list[0]
my_list[2]
my_list[-1]

##items in the list don’t need to be of the same type

miscellaneous_list = ['apple', 3, False, None]

##initialize an empty list with just two squared brackets

empty_list = []

## mutability
fruit = ['apple', 'orange', 'apple']
fruit[2] = 'cherry'
print(fruit)

## length of a list
len(fruit)

```

## Tuple

A tuple is an **ordered** collection, similar to a list, but unlike lists, tuples are **immutable**, which means you cannot change their elements after creating them. 
Tuples are defined using **parentheses ()** and elements are separated by commas. 
Tuples are generally used when you want to create a collection of items that should remain constant throughout the program's execution.


```python

tpl  = ('a', 5, True)
print(tpl)



```

## Set

A set is an **unordered** collection of unique elements. 

Sets **do not allow duplicate values**, and they are **mutable**. 

Sets are defined using **curly braces \{\}**, or you can use the set() constructor.


```python

my_set = {15, 'a', 4, 'k'}
my_empty_set = set()

```


# Dictionary

A dictionary is an **unordered collection** of **key-value pairs**. 
Each **key** in the dictionary must be **unique**, and it is used to access its **corresponding value**. Dictionaries are also **mutable**, so you can add, remove, or modify key-value pairs after creating the dictionary. 
They are defined using curly braces \{\} with key-value pairs.

```python

salary = {'Jane': 100,
          'Jess': 150,
          'Janet' : 200}
          
 my_empty_dict = {}
 
 my_empty_dict = dict()
 
 salary['Jane']
 
 ## 
assign new values to existing key:salary['Jess'] = 175
salary['Jess']
 
```


## Why different data structure?

Besides the forementioned strengths and weaknesses of each data structure, there are several characters making different data structures suitable for different scenarios. 


**Efficient Data Access:** Depending on the nature of data retrieval operations, certain data structures perform better than others. For example, dictionaries provide fast access to values based on keys, making them ideal for tasks that involve frequent data lookups.

I**terating Over Data:** Certain data structures offer fast iteration performance, which is crucial when processing large datasets.

**Sorting and Searching:** Specific data structures, such as binary search trees or sorted arrays, can significantly speed up sorting and searching operations.

The list is not exhausted.















