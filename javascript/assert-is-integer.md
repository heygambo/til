# Assert if input is an integer

When writing a functions it's always a good idea to assert the inputs the function receives.

This tests if a number is an integer without decimal places.

```javascript
function fits(x, y) {
  if (Number.isInteger(y / x)) {
    return 'Fits!';
  }
  return 'Does NOT fit!';
}

console.log(fits(5, 10));
// expected output: "Fits!"

console.log(fits(5, 11));
// expected output: "Does NOT fit!"
```

[source](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/isInteger)
