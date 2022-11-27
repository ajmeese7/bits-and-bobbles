
### JavaScript

```js
var SequenceSum = (function() {
  function SequenceSum() {}

  SequenceSum.showSequence = function(count) {
    if (count < 0) return count + "<" + 0;
    if (count == 0) return count + "=" + 0;

    let sum = 0, str = "";
    for (let i = 0; i <= count; i++) {
      sum += count;
      str += i + ((i != count) ? "+" : " = " + sum / 2);
    }

    return str;
  };

  return SequenceSum;

})();
```
