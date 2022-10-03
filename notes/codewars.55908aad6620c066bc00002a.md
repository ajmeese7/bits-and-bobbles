---
id: b0zlvxpoc62rxu4w6w4hyzs
title: 'Exes and Ohs'
desc: ''
updated: 1664743392504
created: 1590756300000
tags:
  - javascript
  - 7-kyu
  - codewars
  - answer
---

### JavaScript

```js
function XO(str) {
  let numX = 0, numO = 0;
  str = str.toLowerCase();
  for (let i = 0; i < str.length; i++) {
    if (str[i] == 'x') {
      numX++;
    } else if (str[i] == 'o') {
      numO++;
    }
  }

  return numX == numO;
}
```
