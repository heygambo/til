# Pad numbers with leading zeros

There a are several ways how to pad a number with leading zeros.
e.g. so that `1` will become `"0001"`.

There is a new function [String.prototype.padStart](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/padStart) New in EcmaScript 8

```javascript
const smallNumber = 1
const smallNumberPadded = number.toString().padStart(3, '0')
console.log(smallNumberPadded)
// 001

const largerNumber = 11
const largerNumberPadded = number.toString().padStart(3, '0')
console.log(largerNumberPadded)
// 011
```

Note that this will not add the number of leading zeros.
It only adds as many as are needed to get to at least 3 charecters.


---

Custom function

```javascript
function padStart(n, width, z = '0') {
  n = n + '';
  return n.length >= width ? n : new Array(width - n.length + 1).join(z) + n;
}
console.log(padStart('1', 3, '0'))
// 001
console.log(padStart('11', 3, '0'))
// 011
```


[source](https://stackoverflow.com/questions/10073699/pad-a-number-with-leading-zeros-in-javascript)
