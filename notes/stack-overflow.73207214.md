---
id: 35lbr2v59wfvtb19fz9m8ks
title: 'Regex that ignores Latin characters'
desc: 'Combining two regex "^[\x20-\x7E]*$" and "\S(.*\S" into one'
updated: 1664736529944
created: 1659456120000
tags:
  - regex
  - stack-overflow
  - answer
---

> See [here](https://stackoverflow.com/a/73207214/6456163) for the original answer.

One way to do this is to use word boundaries (`\b`) instead of the `\S` anchor:

```regex
^\b[\x20-\x7E]*\b$
```

This would match your given test case `Priya@ #432`, but would not match `priya##23á` or `Priya@ #432 `. You can see an example of this regex in action on Regex101 [here](https://regex101.com/r/bpcUmQ/1).
