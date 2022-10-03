---
id: 4e98qx78q0nyrw2kwibhvdu
title: 'IQ Test'
desc: ''
updated: 1664742097646
created: 1591615740000
tags:
  - javascript
  - 6-kyu
  - codewars
  - answer
---

### JavaScript

```js
function iqTest(numbers) {
  let evens = [], odds = [];
  numbers = numbers.split(' ').map(x => +x);
  numbers.forEach((num) => {
    num % 2 == 0 ? evens.push(num) : odds.push(num);
  });

  return numbers.indexOf(odds.length == 1 ? odds[0] : evens[0]) + 1;
}
```
