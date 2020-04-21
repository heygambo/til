# NPM Package: Casual

Found an easy to use fake library named [Casual](https://www.npmjs.com/package/casual).

Example:
```javascript
casual.define('cat', () => {
  return {
    name: casual.name,
    color: casual.color_name
  }
})

const cat1 = casual.cat
const cat2 = casual.cat
```
