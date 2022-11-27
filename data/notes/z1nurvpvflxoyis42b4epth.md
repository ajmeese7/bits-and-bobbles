
### JavaScript

```js
String.prototype.toJadenCase = function () {
  var words = this.split(' ');
  words.forEach(function(word, index) {
    words[index] = word.charAt(0).toUpperCase() + word.slice(1);
  });

  return words.join(' ');
};
```
