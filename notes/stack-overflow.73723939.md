---
id: s2waxb5srk6yv89sx1q2b4o
title: 'Remove all escape sequences from a string'
desc: 'Capturing a string without escape sequence'
updated: 1664737166183
created: 1663210080000
tags:
  - python
  - regex
  - stack-overflow
  - answer
---

> See [here](https://stackoverflow.com/a/73723939/6456163) for the original answer.

What you're looking for is the `re.sub()` method:

```python
import re

l = ['S;V;iPad\r', 'C;M;mouse pad\r', 'C;C;code swarm\r', 'S;C;OrangeHighlighter']
l_new = [re.sub(r'\r', '', i) for i in l]
print(l_new)
```

This will remove all occurrences of the `\r` escape sequence.
