
### JavaScript

```js
function rankings(arr) {
  var originalArr = [...arr];
  var sortedArray = arr.concat().sort(function (a, b) { return b - a; });
  var rankings = [];

  let len = arr.length;
  for (let i = 0; i < len; i++) {
    rankings[originalArr.indexOf(sortedArray[i])] = i + 1;
  }

  return rankings;
}
```

### Python

```py
def rankings(arr):
    sortedArray = sorted(arr, reverse=True)
    length = len(arr)
    rankings = [None] * length

    for i in range(length):
        rankings[arr.index(sortedArray[i])] = i + 1

    return rankings
```
