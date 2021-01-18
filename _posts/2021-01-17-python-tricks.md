---
title: "Python Tricks"
categories:
  - Blog
tags:
  - Python 
---

Sharing some tricks with python lists

 - Flattening a list of lists.

```python
>>> from itertools import chain
>>> lst = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
>>> list(chain(*lst))
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
