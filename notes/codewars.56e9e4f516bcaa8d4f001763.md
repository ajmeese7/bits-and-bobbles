---
id: epm7jpol7pr5sl6ja2jwuxb
title: 'Sum of numbers from 0 to N'
desc: ''
updated: 1664742290756
created: 1591356660000
tags:
  - javascript
  - 7-kyu
  - codewars
  - answer
---

### JavaScript

```js
var SequenceSum = (function() {
  function SequenceSum() {}

  SequenceSum.showSequence = function(count) {
    if (count < 0) return count + "<" + 0;
    if (count == 0) return count + "=" + 0;

    let sum = 0, str = "";
    for (let i = 0; i <= count; i++) {
      sum += count;
      str += i + ((i != count) ? "+" : " = " + sum / 2);
    }

    return str;
  };

  return SequenceSum;

})();
```
