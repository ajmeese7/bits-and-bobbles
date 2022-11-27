
### JavaScript

```js
function toCamelCase(str) {
  var firstWordCapital = str.charAt(0) == str.charAt(0).toUpperCase();
  var camelCase = "";

  str.split(/[- _]+/).forEach((word, wordIndex) => {
    word.split('').forEach((char, charIndex) => {
      if (wordIndex == 0 && charIndex == 0) {
        camelCase += firstWordCapital ? char.toUpperCase() : char.toLowerCase();
      } else {
        camelCase += charIndex == 0 ? char.toUpperCase() : char.toLowerCase();
      }
    });
  });

  return camelCase;
}
```
