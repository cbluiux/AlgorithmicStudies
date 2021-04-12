```javascript
var twoSum = function (nums, target) {
  const dict = {};

  for (let i = 0; i < nums.length; i++) {
    const remainder = target - nums[i];

    if (Number.isInteger(dict[nums[i]])) {
      return [dict[nums[i]], i];
    }
    dict[remainder] = i;
  }
};
```
