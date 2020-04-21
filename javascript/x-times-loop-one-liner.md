# x times loop one liner

This can be simplified to one line

```javascript
// Environment
const doStuff = () => // doing stuff
const times = 10
```

```javascript
for (let i = 0; i < times, ++i) {
  doStuff()
}
```

using `Array` and the spread operator

```javascript
[...Array(times)].map(doStuff)
```

This is especially useful the same function should be called multiple times.


[source](https://stackoverflow.com/a/37417004/1224625)
