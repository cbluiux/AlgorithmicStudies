```javascript
// PLAIN STACK SOLUTION

var backspaceCompare = function (S, T) {
  return backSpacer(S) == backSpacer(T);
};

function backSpacer(str) {
  let stack = [];
  for (let i of str) {
    if (i !== '#') {
      stack.push(i);
    } else {
      stack.pop(i);
    }
  }
  return stack.join('');
}

// REDUCE STACK SOLUTION

var backspaceCompare = function (S, T) {
  const helper = (string) => {
    return string
      .split('')
      .reduce((result, curr) => {
        curr === '#' ? result.pop() : result.push(curr);
        return result;
      }, [])
      .join('');
  };
  return helper(S) === helper(T);
};

// TWO POINTER NO EXTRA SPACE

const backspaceCompare = (s, t) => {
  let sPointer = s.length - 1;
  let tPointer = t.length - 1;
  let sCount = 0;
  let tCount = 0;

  while (sPointer >= 0 || tPointer >= 0) {
    let sItem = s[sPointer];
    let tItem = t[tPointer];

    if (sItem === '#') {
      sPointer--;
      sCount++;
    } else if (tItem === '#') {
      tPointer--;
      tCount++;
    } else if (sCount > 0) {
      sCount--;
      sPointer--;
    } else if (tCount > 0) {
      tCount--;
      tPointer--;
    } else if (sPointer >= 0 && tPointer >= 0 && sItem !== tItem) {
      return false;
    } else if (sPointer >= 0 !== tPointer >= 0) {
      return false;
    } else {
      sPointer--;
      tPointer--;
    }
  }
  return true;
};
```
