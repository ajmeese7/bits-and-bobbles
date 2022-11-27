
### JavaScript

```js
function smaller(nums) {
  var smallerNums = [];
  for (var index = 0; index < nums.length; index++) {
    var numToCheck = nums[index];
    var smallerCount = 0;
    for (var remainingIndices = nums.length - index; remainingIndices > 0; remainingIndices--) {
      if (nums[index + remainingIndices] < numToCheck) smallerCount++;
    }

    smallerNums.push(smallerCount);
  }

  return smallerNums;
}
```
