---
id: r6eors1zq0u63mw7yddvpda
title: 'The Hashtag Generator'
desc: ''
updated: 1664741436286
created: 1662152100000
tags:
  - python
  - 5-kyu
  - codewars
  - answer
---

### Python

```py
def generate_hashtag(s):
    capital_sentence = "".join(w.capitalize() for w in s.split())
    length = len(capital_sentence)
    if length == 0 or length > 140:
        return False

    return "#" + capital_sentence
```
