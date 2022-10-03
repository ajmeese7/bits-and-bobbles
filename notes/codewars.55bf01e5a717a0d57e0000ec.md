---
id: qu6p8fk72ugtfgphaigohkn
title: 'Persistent Bugger.'
desc: ''
updated: 1664742350851
created: 1591290240000
tags:
  - javascript
  - 6-kyu
  - codewars
  - answer
---

### JavaScript

```js
function persistence(num) {
  var sNumber = num.toString(), result = 1, numTimes = 0;
  for (let i = 0; i < sNumber.length; i++) {
    if (sNumber.length > 1) numTimes++;

    for (let j = 0; j < sNumber.length; j++) {
      result *= parseInt(sNumber.charAt(j));
    }

    sNumber = result.toString(), i = 0, result = 1;
  }

  return numTimes;
}
```
