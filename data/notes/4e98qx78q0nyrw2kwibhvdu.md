
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
