
### JavaScript

```js
function XO(str) {
  let numX = 0, numO = 0;
  str = str.toLowerCase();
  for (let i = 0; i < str.length; i++) {
    if (str[i] == 'x') {
      numX++;
    } else if (str[i] == 'o') {
      numO++;
    }
  }

  return numX == numO;
}
```
