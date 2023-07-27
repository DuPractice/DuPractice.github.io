---
title: When a R user began coding with Python I
date: 2023-07-20T16:00:21-04:00
author: Xinting Du
slug: bookdown-tips
draft: false
toc: true
tags: Python
---


Excited to start my journey in Python!

I am a R user and always tell myself it is already enough to master one language. But this summer I attended to the [ICPSR Sumer Program in Quantitative Methods](https://www.icpsr.umich.edu/web/pages/sumprog/) and enrolled several exciting courses, such as Text Analysis and the Introduction to Python. I thought it’s time to learn something new!

1. Why Python?

Actually, I learn Python because I want to push forward one of my text-analysis projects, which I need to scrap data from Weibo first. And Python is useful to conduct web scraping.

2. Why this series of blog?

I try to write down and summarize this learning process, including What I had learnt, my random thoughts, etc. If you are also a R user and try to learn Python. Hopefully, this document will encourage you to take the first step without no hesitation!

3. A Claim

I gave credit to [Dr. Omer F. Yalcin](https://omerfyalcin.com/). With his enthusiasim in teaching and clear demonstration, I could learn in a smooth pace.
Also, I will collect other useful materials and add the reference link later!



## Getting started with Python

My recommendations for getting started are as follows:

[Google Colab](https://colab.research.google.com): quickly start writing code in browser.

[Anaconda](https://www.anaconda.com): if you want to work locally instead to easily install Python & packages to get Spyder to write code locally.

## Let's start coding

Python manipulates **data objects**, and objects have a **type**. 

Objects are: scalar (int, float, bool, and NoneType), or non-scalar

```python
## use type() to get the type of an object
type(3)
type(4.2)
type(False)
type(None)

## Objects of different types can be converted to one another

int(3.6)
float(4)
```

## Math Operations

| Operator          | Name       |  Example |
| -----------------|:---------------:| -----------------|
| +     | Addition      |  x+y |
| -  | Subtraction  | x-y |
| *| Multiplication        |  x*y|
| /| Division  | x/y|
| \% | Modulus | x\%y|
|**|Exponentiation| x**y|
|//| Floor disvision | x//y|

## Variables and Values

Equal sign (=) is used for assignment of a value to a variable

```python

pi = 3.14159
radius = 5

pring(pi)
pring(radius)

```
# String data 

```python
greeting = "Hello! How are you"
who = 'Anastasia'

## Concatenate with + (very similar to paste0() in R)

greeting + ' ' + who + '?'

## print() can print strings and other things

n_apples = 3
print('I ate', n_apples, ' apples.')

## I also find input() a very interesting function, I havent seen a similar one in R

text = input("Tell me something...")
print("So you're saying", text)

```

## Comparison Operators and Logical Operators
The comparison operators in Python is the same with those in R

```python
var1 > var2
var1 >= var2
var1 < var2
var1 <= var2
var1 == var2
var1 != var2

## And it will return a Boolean: True or False 

## **not**, **or**, **and** are special words for logical operators. This part is very different from R. Remeber in R, we use \| indicating or,  \& indicating ang, \!= indicating not.

 # How did you commute today?
bike = True
bus = False
print(bike or bus)
print(bike and bus)
```

## Branching: if, else, elif

The syntax of using if is very similar to the R. 

```python
number = 12
if number % 2 == 0:
    print("Number is even.")
else:
    print("Number is odd.")
    
 ```
 
 ```python
 
  number = 0
if number > 0:
    print("Positive number")
elif number == 0:
    print('Zero')
else:
    print('Negative number')
print('This statement is always executed')

```
## Loops: for

for loops are useful when number of iterations are known.

 ```python
 
for i in range(5):
  print(i)
	
	
for i in range(11, 15):
  print(i)
  
for i in range(10, 30, 5):
  print(i)
  
 ## range(start, stop, step)
 
 for char in 'MICHIGAN':
    print(char + "!")

## can iterate over other things


for i in range(1, 4):
    for j in range(1, 4):
        if i == 2 and j == 2:
            break
print(i, j)
  

```







