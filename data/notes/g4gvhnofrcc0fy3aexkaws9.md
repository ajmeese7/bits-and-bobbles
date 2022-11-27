
### JavaScript

```js
function add() {
  var args = [...arguments];
  function addReturn() {
    // Recursion passing back previous total and remaining args
    return add(...args, ...arguments);
  }

  addReturn.value = args.reduce((total, val) => total + val);
  addReturn.valueOf = () => { return addReturn.value };
  return addReturn;
}
```
