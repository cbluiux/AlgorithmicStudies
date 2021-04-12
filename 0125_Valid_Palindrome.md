```javascript
// TWO POINTER SOLUTION

function validPalindrome(string) {
  //use regex to remove any spaces or special symbols & then lowercase the whole string
  //term for removing all of the things you don't want is Sanitize?
  let newString = string.replace(/[^A-Za-z0-9]/g, '').toLowerCase();
  let left = 0;
  let right = newString.length - 1;

  while (left < right) {
    //if at any point left and right don't match return false
    if (newString[left] !== newString[right]) {
      return false;
    }
    //keep searching by moving the pointers
    left++;
    right--;
  }
  return true;
}
```
