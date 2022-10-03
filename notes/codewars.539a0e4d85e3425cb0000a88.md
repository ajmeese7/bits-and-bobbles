---
id: g4gvhnofrcc0fy3aexkaws9
title: 'A Chain adding function'
desc: ''
updated: 1664742244464
created: 1591369200000
tags:
  - javascript
  - 5-kyu
  - codewars
  - answer
---

### JavaScript

```js
function add() {
  var args = [...arguments];
  function addReturn() {
    // Recursion passing back previous total and remaining args
    return add(...args, ...arguments);
  }

  addReturn.value = args.reduce((total, val) => total + val);
  addReturn.valueOf = () => { return addReturn.value };
  return addReturn;
}
```
