# Javascript

[[TOC]]

## Variables

### [var](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var)
Function-scoped / global-scoped variable

### [let](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let)
Block-scoped variable.<br>
Unless `var`, allow to free up RAM insted of keeping unused variables.


```javascript
let a = 10
let b = a
```
_`let` variables are independant: two entries are stored in memory, each one with value "10"_


### [const](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const)
Block-scoped constant<br>
Variable can't be redeclared, its value can't be changed.

```javascript
const array = [1,2,3];
array[0] = 9 // [9,2,3]
```
_Arrays can't be redefined, but its values can. To avoid this, use `Object.freeze`_


## Arrays
Complexe types. Link a reference insted of storing a value.
```javascript
let array1 = [1,2,3];
let array2 = array1;
array1.push(5); // [1,2,3,5]
console.log(array2); // [1,2,3,5]
```
_Two references are linked to the same value_
```javascript
let array1 = array2 // create alias
```

### Clone array
```javascript
let array2 = array1.map();
// or
let array1 = [...array2];
```