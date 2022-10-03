---
id: kjxidok94ab149sir22q0ww
title: 'How many are smaller than me?'
desc: ''
updated: 1664742534990
created: 1591116360000
tags:
  - javascript
  - 7-kyu
  - codewars
  - answer
---

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
