---
id: ziu5oe8967pswbqdzqnedje
title: Split Strings
desc: ''
updated: 1664741495318
created: 1661990460000
tags:
  - python
  - 6-kyu
  - codewars
  - answer
---

### Python

```py
def solution(s):
    solution_array = []
    for i in range(0, len(s), 2):
        string = s[i] + (s[i+1] if i+1 < len(s) else '_')
        solution_array.append(string)
    return solution_array
```
