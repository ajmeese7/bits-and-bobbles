
### JavaScript

```js
function chooseBestSum(maxTotal, numTowns, distances) {
  // https://stackoverflow.com/a/42531964/6456163
  let combinations = new Array(1 << distances.length).fill().map(
    (e1,i) => distances.filter((e2, j) => i & 1 << j));
  let routes = combinations.filter(a => a.length == numTowns);
  let maxSum = 0;

  for (let i = 0; i < routes.length; i++) {
    let sum = routes[i].reduce((acc, val) => acc + val);
    if (sum > maxSum && sum <= maxTotal) maxSum = sum;
  }

  return maxSum != 0 ? maxSum : null;
}
```
