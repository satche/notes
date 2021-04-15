# Arrays
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

## Clone array
```javascript
let array2 = array1.map();
// or
let array1 = [...array2];
```