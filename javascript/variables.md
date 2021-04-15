# Variables

## [var](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var)

Function-scoped / global-scoped variable

## [let](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let)

Block-scoped variable.<br>
Unless `var`, allow to free up RAM insted of keeping unused variables.

```javascript
let a = 10;
let b = a;
```

_`let` variables are independant: two entries are stored in memory, each one with value "10"_

## [const](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const)

Block-scoped constant<br>
Variable can't be redeclared, its value can't be changed.

```javascript
const array = [1, 2, 3];
array[0] = 9; // [9,2,3]
```

_Arrays can't be redefined, but its values can. To avoid this, use `Object.freeze`_
