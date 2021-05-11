# Pair w/ Target Sum

```javascript
const pair_with_target_sum = function(arr, target_sum) {
  // TODO: Write your code here
  let left = 0
  let right = arr.length - 1

  while (left < right) {
    let lval = arr[left]
    let rval = arr[right]
    let currSum = lval + rval

    if (currSum === target_sum) {
      return [left, right]
    }

    if (currSum < target_sum) {
      left++
    } else {
      right--
    }
  }

  return [-1, -1];
}
```

# Remove Duplicates

```javascript
function remove_duplicates(arr) {
  // index of the next non-duplicate element
  let nextNonDuplicate = 1;

  let i = 1;
  while (i < arr.length) {
    if (arr[nextNonDuplicate - 1] !== arr[i]) {
      arr[nextNonDuplicate] = arr[i];
      nextNonDuplicate += 1;
    }
    i += 1;
  }
  return nextNonDuplicate;
}
```
# Squaring Sorted Array

```javascript
function make_squares(arr) {
  const n = arr.length;
  squares = Array(n).fill(0);
  let highestSquareIdx = n - 1;
  let left = 0,
    right = n - 1;

  while (left <= right) {
    let leftSquare = arr[left] * arr[left],
      rightSquare = arr[right] * arr[right];

    if (leftSquare > rightSquare) {
      squares[highestSquareIdx] = leftSquare;
      left += 1;
    } else {
      squares[highestSquareIdx] = rightSquare;
      right -= 1;
    }
    highestSquareIdx -= 1;
  }
  return squares;
}
```

