---
id: zsuodqfuzaagf0pxavo905g
title: 'Match Groovy package semver with regex'
desc: 'Groovy regex not matching'
updated: 1664736530164
created: 1660239360000
tags:
  - regex
  - groovy
  - stack-overflow
  - answer
---

> See [here](https://stackoverflow.com/a/73321649/6456163) for the original answer.

I modified your regex to match the package naming convention, you can see a working example [here](https://regex101.com/r/h4o5tS/1):

```regex
((.*)\.\d+\.\d+\.\d+-\d+)\.x86_64\.rpm
```
