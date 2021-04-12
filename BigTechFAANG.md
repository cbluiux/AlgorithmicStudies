# Mastering the Coding Interview: Big Tech (FAANG) Interviews

## Arrays: Question #1 Google Interview Question Two Sum (Easy)

```javascript
var twoSum = function (nums, target) {
  numsIndexes = {};

  for (let i = 0; i < nums.length; i += 1) {
    //Iterate through array & compute currentDifference

    let currentElement = nums[i];
    let currentDifference = target - currentElement;

    //If currentDifference exists in hashTable and currentElementIndex !== hashTable[currentDifference], return the indices of each element.

    if (
      numsIndexes[currentDifference] !== undefined &&
      numsIndexes[currentDifference] !== i
    ) {
      return [numsIndexes[currentDifference], i];
    } else {
      //If currentDifference does not exist or the indices of both elements are equal, move to the next element in the array.

      numsIndexes[nums[i]] = i;
    }
  }
};
```

## Stacks - Question #10 - Valid Parentheses (Easy)

```javascript
/*
inputA = "{}[]" -> true
inputB = "{[}]" -> false
inputC = "{{}()[]}" -> true
inputD = "" -> true
inputE = "][][" -false

edge cases
stack = [] //variant
hashmap = {} //invariant
for(i < s.length)




*/

var isValid = function (s) {
  // edge cases
  if (s.length === 0) return true;
  if (s.length === 1) return false;
  if (s.length % 2 !== 0) return false;

  let stack = [];
  const hashMap = {
    '}': '{',
    ')': '(',
    ']': '[',
  };

  for (var i = 0; i < s.length; i++) {
    const currChar = s[i];
    const topStack = stack[stack.length - 1];
    const delChar = hashMap[currChar];

    if (delChar) {
      if (delChar === topStack) {
        stack.pop();
      } else {
        return false;
      }
    } else {
      stack.push(currChar);
    }
  }

  return !stack.length;
};
```

## Stacks - Extra Credit - Asteroid Collision (Medium)

```javascript
/*



*/
var asteroidCollision = function (asteroids) {
  let i = 0;
  let stack = [];

  while (i < asteroids.length) {
    let curr = asteroids[i];
    let topStack = stack[stack.length - 1];

    if (curr >= 0 || !stack.length || topStack < 0) {
      stack.push(asteroids[i++]);
    } else if (curr + topStack < 0) {
      // current negative is bigger than previous positive
      stack.pop();
    } else if (curr + topStack === 0) {
      // same size
      stack.pop();
      i++;
    } else {
      // current negative is smaller than previous positive
      i++;
    }
  }

  return stack;
};
```

## Stacks - Question #11 - Minimum Brackets To Remove (Medium)

```javascript

```

## Recursion (Sorting and Hoare's QuickSelect) - Question #13 - Kth Largest Element

```javascript
/*
Brute Force Approach:
Sort nums A-Z - O(n log(n)) time // O(n) space
iterate through the new sorted array to drop doubles - O(n) time // O(1) space
access kth largest by (.length - k) designation



*/

var findKthLargest = function (nums, k) {
  let sorted = nums.sort((a, b) => a - b);

  console.log(sorted);
  return sorted[sorted.length - k];
};
```
