
### JavaScript

```js
var moveZeros = function (arr) {
  // To retest same index in case the new value is also a 0
  // Didn't want to think of a fancy way to retest indexes the first go-around
  for (let lazy = 0; lazy < 10; lazy++) {
    for (let i = 0; i < arr.length; i++) {
      if (arr[i] === 0) {
        arr.splice(i, 1);
        arr.push(0);
      }
    }
  }

  return arr;
}
```
