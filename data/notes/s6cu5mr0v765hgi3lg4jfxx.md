
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
