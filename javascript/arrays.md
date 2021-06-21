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

_[Spread operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax)_

```javascript
let array1 = [1, 2];
let array2 = [...array1, 3, 4]; // [1,2,3,4]
```

## Methods

### [`array.filter()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)

_Create new array with all elements that pass the test (the function in argument)_

```javascript
let array1 = [1, 2, 3];
let array2 = array1.filter(element => element < 3); // [1, 2]
```

### [`array.map()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)

_Run a given function on each item of an array_

```javascript
let array1 = [1, 2, 3];
let array2 = array1.map(element => element * 2); // [2, 4, 6]
```

_Define object_

```javascript
let array1 = ["a", "b", "c"];
let array2 = array.map((element, index) => ({
	[index]: element,
})); // [{0:a} {1:b} {2:c}]
```

### [`array.reduce()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce) / [`array.reduceRight()`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global_Objects/Array/ReduceRight)

_Run a given function on each item regarding the previous result. Can optionaly define the initial value to start with_

```javascript
let array1 = [1, 2, 3];
const sum = array1.reduce((prev, curr) => prev + curr); // 6
const sum2 = array1.reduce((prev, curr) => prev + curr, 4); // 10
```

![](images/reduce.png)

### [`array.sort()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)

_Sort elements of an array and return the sorted array. Take a facultative comparaison function, which handle two arguments: the first element of the array compared with the second one_

```javascript
let array1 = [3, 2, 1];
array1.sort(); // [1,2,3]
array1.sort((firstEl, secondEl) => secondEl - firstEl); // [3,2,1]
```
