# Objects

```javascript
const obj = { a: "foo", b: "bar" };
console.log(obj.a); // foo
```

_Define with a variable_

```javascript
let key = a;
let obj = { [key]: "foo" }; // {a: foo}
```

_[Spread operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax)_

```javascript
let obj = { a: "foo" };
let obj2 = [...obj, b: "bar"]; // { a:"foo", b:"bar" }
```

## Methods

### Object to array

_[Object.key](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/keys), [Object.value](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/values), [Object.entries](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/entries)_

```javascript
const obj = { a: "foo", b: "bar" };
Object.key(obj); // ["a", "b"]
Object.value(obj); // ["foo", "bar"]
Object.entries(obj); // [["a", "foo"] ["b", "bar" ]]
```

## How to

### Count number of element from an array

```javascript
const elements = ["apple", "apple", "lime", "lime", "orange"];
const obj = {};
elements.forEach(element => {
	obj[element] = (obj[element] || 0) + 1;
});
console.log(obj); // {apple: 2, lime: 2, orange: 1}
```
