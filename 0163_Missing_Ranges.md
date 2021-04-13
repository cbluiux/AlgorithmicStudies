```javascript
var findMissingRanges = function (nums, lower, upper) {
  let arrw = '->';
  let ranges = [];
  nums.unshift(lower - 1);
  nums.push(upper + 1);

  for (let i = 1; i < nums.length; i++) {
    let curr = nums[i];
    let previous = nums[i - 1];

    if (previous === curr - 2) {
      ranges.push('' + (previous + 1));
    } else if (curr - previous > 2) {
      ranges.push('' + (previous + 1) + arrw + (curr - 1));
    }
  }
  return ranges;
};
```
