
### JavaScript

```js
function decipherThis(str) {
  var words = str.split(" ");

  for (var i = 0; i < words.length; i++) {
    var word = words[i];
    var charCode = word.match(/\d+/)[0];
    word = word.replace(charCode, '');

    var firstCharacter = String.fromCharCode(charCode);
    word = firstCharacter + word;

    if (word.length > 2) {
      var lastChar = word.charAt(word.length - 1);
      var secondChar = word.charAt(1);
      word = word.replaceAt(1, lastChar);
      word = word.replaceAt(word.length - 1, secondChar);
    }

    words[i] = word;
  }

  return words.join().replaceAll(",", " ");
};

String.prototype.replaceAt = function(index, replacement) {
    return this.substr(0, index) + replacement + this.substr(index + replacement.length);
}

// Using the lazy way to replace the random commas with spaces; will break eventually
String.prototype.replaceAll = function(search, replacement) {
  var target = this;
  return target.replace(new RegExp(search, 'g'), replacement);
};
```
