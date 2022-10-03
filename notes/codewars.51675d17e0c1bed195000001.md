---
id: s6cu5mr0v765hgi3lg4jfxx
title: 'Largest 5 digit number in a series'
desc: ''
updated: 1664743073494
created: 1590763560000
tags:
  - javascript
  - 7-kyu
  - codewars
  - answer
---

### JavaScript

```js
function solution(digits) {
  var greatestNum = 0, sequenceLength = 5;
  for (var i = 0; i < digits.length - (sequenceLength - 1); i++) {
    var num = "";
    for (var j = 0; j < sequenceLength; j++) {
      num += digits[i + j];
    }

    num = parseInt(num);
    if (num > greatestNum) greatestNum = num;
  }

  return greatestNum;
}
```
