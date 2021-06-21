# Objects

```javascript
const obj = {
	a: foo
	b: bar
}

console.log(obj.a) // foo
Object.keys(obj) // ["a", "b"]
```

_Define with a variable_

```javascript
let key = foo;
let obj = { [key]: bar }; // {foo: bar}
```

## Methods

### Object.keys

_Get keys of object_

```javascript
const obj = { a: foo, b: bar };
Object.key(obj); // ["a", "b"]
```

## How to

### Count number of element from an array

```javascript
const elements = ["apple", "apple", "lime", "lime", "orange"];
const object = {};
elements.forEach(element => {
	object[element] = (object[element] || 0) + 1;
});
console.log(object); // {apple: 2, lime: 2, orange: 1}
```
