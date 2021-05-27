# Variables

## [var](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var)

Function-scoped / global-scoped variable

## [let](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let)

Block-scoped variable.<br>
Unless `var`, allow to free up RAM insted of keeping unused variables.

_`let` variables are independant: two entries are stored in memory, each one with value "10"_

```javascript
let a = 10;
let b = a;
```

## [const](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const)

Block-scoped constant.<br>
Its value can't be changed through reassignment, and it can't be redeclared.<br>

_Can take the role of a constant (uppercase, more like a setting or configuration value), or a immutable variable (lowercase, more like a value we don't want it to change)._

```javascript
const WIDTH = 10; // constants
const domElement = document.createElement("div"); // immutable variable
```

_Arrays can't be redefined, but its values can. To avoid this, use `Object.freeze`_

```javascript
const array = [1, 2, 3];
array[0] = 9; // [9,2,3]
```
