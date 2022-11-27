
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
