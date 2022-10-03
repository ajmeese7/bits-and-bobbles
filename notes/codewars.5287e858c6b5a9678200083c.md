---
id: 2qi7ewd2e3j0s7wndfb1i7x
title: 'Does my number look big in this?'
desc: ''
updated: 1664741971925
created: 1591636200000
tags:
  - javascript
  - coffeescript
  - 6-kyu
  - codewars
  - answer
---

### JavaScript

```js
function narcissistic(value) {
  let digits = value.toString().split('').map(x => parseInt(x));
  let len = digits.length, sum = 0;
  digits.forEach((num) => sum += Math.pow(num, len));

  return sum == value;
}
```

### CoffeeScript

```coffee
narcissistic = (value) ->
  digits = value.toString().split('').map (x) -> parseInt(x)
  len = digits.length; sum = 0;
  digits.forEach((num) => sum += Math.pow(num, len));

  return sum == value;
```
