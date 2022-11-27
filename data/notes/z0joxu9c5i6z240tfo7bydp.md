
### JavaScript

```js
function findEvenIndex(arr) {
  for (const index in arr) {
    let workingArr = [...arr];
    workingArr[index] = 0;

    const firstHalf = workingArr.slice(0, index);
    const secondHalf = workingArr.slice(index);

    const firstHalfSum = firstHalf.reduce((acc, num) => acc + num, 0);
    const secondHalfSum = secondHalf.reduce((acc, num) => acc + num, 0);

    if (firstHalfSum === secondHalfSum) return parseInt(index);
  }

  return -1;
}
```
