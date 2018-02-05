# Let and const

If we use `let` and `const` scope is limited to any blocks {}

## const

We can't redefine `const` variable. But if we have an object we can change and add additional properties

```javascript
const obj {
	a: 1,
	b: 2
}
obj.a = 2;
obj.c = 3;
```
