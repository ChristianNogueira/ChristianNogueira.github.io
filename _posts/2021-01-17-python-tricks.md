---
title: "Python Tricks"
categories:
  - Blog
tags:
  - Python 
---

Sharing some useful tricks with python 

 - Flattening a list of lists.

```python
from itertools import chain

def flat_list(lst):
    return list(chain(*lst))

>>> flat_list([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
[1, 2, 3, 4, 5, 6, 7, 8, 9]
```

 - Keep a max quantity of elements in a list

```python
def limit_lst(lst, max_e):
     return [x for i, x in enumerate(lst) if lst[:i].count(x) < max_e]

>>> limit_lst([1, 2, 3, 2, 3, 4, 2], 2)
[1, 2, 3, 2, 3, 4]
```

 - Distinct permutation of a string

```python
from itertools import permutations

def permutations(string):
    return list("".join(p) for p in set(permutations(string)))

>>> permutations('aabb')
['aabb', 'abab', 'abba', 'baab', 'baba', 'bbaa']
```

 - Unpack string or list into string with placeholders 

```python
def fill_placeholder(strng, placeholder, values):
    return strng.replace(placeholder, "{}").format(*values)

>>> fill_placeholder("H**lo *or*d", "*", "elWl")
'Hello World'
>>> fill_placeholder("H**lo *or*d", "*", ["e", "l", "W", "l"])
'Hello World'
```
