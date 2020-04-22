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

---

UPDATE: This will not work using TypeScript because it doesn't understand that `casual.cat` is a thing now.

When using TypeScript it works by creating functions like so:

```typescript
const makeCat = (): ICat => {
  return {
    name: casual.name,
    color: casual.color_name
  }
})

const cat1 = makeCat()
const cat2 = makeCat()
```
