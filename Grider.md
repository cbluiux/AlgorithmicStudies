## Intro Problems

### Fibonacci Sequence

```javascript
const fib = (n) => {
  if (n < 2) {
    return n;
  };
  return (fib(n - 1) + fib(n - 2));
};
```

### FizzBuzz

```javascript
var fizzBuzz = function(n) {
  let result = [];
  for(let i = 1; i <= n; i++){
    let temp = '';

    temp += i % 3 ? '' : 'Fizz';
    temp += i % 5 ? '' : 'Buzz';

    if (!temp) temp += i;

    result.push(temp);
  }

  return result;
};
```




## String Reversal

### Reverse a string

```javascript
function reverse(str) {
    return str
        .split('')
        .reverse()
        .join('');
};
```

```javascript
function reverse(str) {
    let reversed = [];

    for (let i = 0; i < str.length; i++) {
        reversed.unshift(str[i]);
    };
    return reversed.join('');
};
```

```javascript
function reverse(str) {
    return str
      .split('')
      .reduce((reversed, character) => {
        return character + reversed;
      }, '');
};
```
