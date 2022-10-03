---
id: r6wl9fzetomjmlnjfddoysm
title: 'Create Phone Number'
desc: ''
updated: 1664742760689
created: 1591020540000
tags:
  - javascript
  - php
  - 6-kyu
  - codewars
  - answer
---

### JavaScript

```js
function createPhoneNumber(numbers) {
  return `(${numbers.getRangeAsString(0,2)}) ${numbers.getRangeAsString(3,5)}-${numbers.getRangeAsString(6,9)}`;
}

Array.prototype.getRangeAsString = function(start, stop) {
  var target = this, string = "";
  for (let index = start; index <= stop; index++) {
    string += target[index];
  }

  return string;
};
```

### PHP

```php
function createPhoneNumber($numbersArray) {
  $numbers = implode("", $numbersArray);
  return "(" . substr($numbers,0,3) . ") " . substr($numbers,3,3) . "-" . substr($numbers,6,4);
}
```
