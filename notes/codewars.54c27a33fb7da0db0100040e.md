---
id: ltoev3uyh6pfgosn5bfbqnp
title: You're a square!
desc: ''
updated: 1664757379061
created: 1590668640000
tags:
  - javascript
  - 7-kyu
  - codewars
  - answer
---

### JavaScript

```js
var isSquare = function(n) {
  const sign = Math.sign(n);
  return sign != -1 && Math.sqrt(n) % 1 === 0;
}
```
