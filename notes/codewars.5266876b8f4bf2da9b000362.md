---
id: a0ftzxkuq0o9nuwwmisr9e8
title: 'Who likes it?'
desc: ''
updated: 1664757472229
created: 1590667320000
tags:
  - javascript
  - 6-kyu
  - codewars
  - answer
---

### JavaScript

```js
function likes(names) {
  if (names === undefined || names.length == 0) {
    return "no one likes this";
  } else if (names.length == 1) {
    return names[0] + " likes this";
  } else if (names.length == 2) {
    return names[0] + " and " + names[1] + " like this";
  } else if (names.length == 3) {
    return names[0] + ", " + names[1] + " and " + names[2] + " like this";
  } else {
    const numNamesRemaining = names.length - 2;
    return names[0] + ", " + names[1] + " and " + numNamesRemaining + " others like this";
  }
}
```
