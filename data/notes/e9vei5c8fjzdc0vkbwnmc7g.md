
### JavaScript

```js
function disemvowel(str) {
  const regex = /[aeiou]/gi;
  str = str.replace(regex, '');

  return str;
}
```
