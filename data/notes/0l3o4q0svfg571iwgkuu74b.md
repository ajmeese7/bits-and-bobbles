
### JavaScript

```js
function findMissingLetter(array) {
  let previousCharCode = '';
  for (let i = 0; i < array.length; i++) {
    const charCode = array[i].charCodeAt(0);
    if (previousCharCode != '' && charCode != previousCharCode + 1) {
      return String.fromCharCode(charCode - 1);
    } else {
      previousCharCode = charCode;
    }
  }

  return ' ';
}
```
