``` javascript
var isValid = function (s) {
  const stack = [];
  const complement = {
    ')': '(',
    '}': '{',
    ']': '[',
  };

  for (let char of s) {
    if (!complement[char]) stack.push(char);
    else if (stack.pop() !== complement[char]) return false;
  }
  return stack.length === 0;
};

```

``` javascript

// 1
if (s.length === 0) return true
if (s.length === 1) return false
if (s.length % 2 !== 0) return false

const dictionary = {
	'}': '{',
	')': '(',
	']': '['
}
const stack = []

for (let i = 0; i < s.length; i++) {
	const currChar = s[i]
	const lastChar = stack[stack.length - 1]
	const delChar = dictionary[currChar]

	if (delChar) {
		// 2
		if (delChar === lastChar) {
			stack.pop()
		} else {
			return false
		}
	} else {
		stack.push(currChar)
	}
}

// 3
return !stack.length

```
