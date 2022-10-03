---
id: kc43zsaiypaamv7xghep45q
title: 'Polydivisible Numbers'
desc: ''
updated: 1664741601253
created: 1591764120000
tags:
  - python
  - 7-kyu
  - codewars
  - answer
---

### Python

```py
def polydivisible(x):
    isPoly = True
    for numDigits in range(1, len(str(x)) + 1):
        num = int(str(x)[:numDigits])
        if num % numDigits is not 0:
            isPoly = False
            break
    return isPoly
```
