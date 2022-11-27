
### JavaScript

```js
var isSquare = function(n) {
  const sign = Math.sign(n);
  return sign != -1 && Math.sqrt(n) % 1 === 0;
}
```
