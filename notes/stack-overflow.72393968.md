---
id: sm5ov1hnxcvvp264vn3fgns
title: 'Access the `location` prop in Gatsby'
desc: 'location props in gatsby is not defined'
updated: 1664736529997
created: 1653591960000
tags:
  - gatsby
  - javascript
  - react
  - stack-overflow
  - answer
---

> See [here](https://stackoverflow.com/a/72393968/6456163) for the original answer.

You should have the `location` variable already defined, it is likely in the global scope so you don't need to pass it as a parameter to the function. Try just using the variable and see if that works.
