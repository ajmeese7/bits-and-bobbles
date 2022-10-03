---
id: 8l4pjwo1pmlp8d71d8zlj3z
title: 'Counting Duplicates'
desc: ''
updated: 1664741585661
created: 1662154140000
tags:
  - python
  - 6-kyu
  - codewars
  - answer
---

### Python

```py
from collections import Counter

def duplicate_count(text):
    if not text: return 0
    frequencies = Counter(text.lower())
    return len(list(
        filter(lambda x: x > 1, frequencies.values())
    ))
```
