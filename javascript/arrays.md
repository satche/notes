# Arrays

Complexe types. Link a reference insted of storing a value.

```javascript
let array1 = [1, 2, 3];
let array2 = array1;
array1.push(5); // [1,2,3,5]
console.log(array2); // [1,2,3,5]
```

_Two references are linked to the same value_

```javascript
let array1 = array2; // create alias
```

_Clone array with map or with [spread operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax)_

```javascript
let array2 = array1.map();
// or
let array1 = [...array2];
```

## Methods

### [`array.filter()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)

_Create new array with all elements that pass the test (the function in argument)_

```javascript
let array1 = [1, 2, 3];
let array2 = array1.filter(item => item < 3); // [1, 2]
```

### [`array.map()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)

_Run a given function on each item of an array_

```javascript
let array1 = [1, 2, 3];
let array2 = array1.map(item => item * 2); // [2, 4, 6]
```

_Redefine object_

```javascript
let data = { a: foo, b: bar };
data = data.map(item => ({
	hello: item.a,
	world: item.b,
})); // { hello: foo, world: bar }
```

### [`array.reduce()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce) / [`array.reduceRight()`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global_Objects/Array/ReduceRight)

_Run a given function on each item regarding the previous result. Can optionaly define the initial value to start with_

```javascript
let array1 = [1, 2, 3];
const sum = array1.reduce((prev, curr) => prev + curr); // 6
const sum2 = array1.reduce((prev, curr) => prev + curr, 4); // 10
```

![](data:image/png;base64,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)

### [`array.sort()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)

_Sort elements of an array and return the sorted array. Take a facultative comparaison function, which handle two arguments: the first element of the array compared with the second one_

```javascript
let array1 = [3, 2, 1];
array1.sort(); // [1,2,3]
array1.sort((firstEl, secondEl) => secondEl - firstEl); // [3,2,1]
```
