
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
