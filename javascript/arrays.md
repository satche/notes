# Arrays

Complexe types

Link a reference insted of storing a value.

```javascript
let array1 = [1, 2, 3];
let array2 = array1; // array2 is an alias of array1

array1.push(5); // [1,2,3,5]
console.log(array2); // [1,2,3,5]
```

[Spread operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax)

```javascript
let array1 = [1, 2];
let array2 = [array1, 3, 4]; // [ [1,2], 3,4]
let array3 = [...array1, 3, 4]; // [1,2,3,4]
```

## Methods

### Add and merge stuff

#### [`array.push()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/push)

Add element(s) to array and store the length

```javascript
let array = [1, 2];
let array2 = [3, 4];
let arrayLength = array.push(...array2); // 4
console.log(array); // [1, 2, 3, 4]
```

#### [`array.concat()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/concat)

Merge arrays to a new one

```javascript
let array = [1, 2];
let array2 = [3, 4];
let arrayMerged = array.concat(array2); // [1,2,3,4]
```

#### [`array.join()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/join)

Join element of an array and return a string

```javascript
let array = [1, 2, 3, 4];
let string = array.join("+"); // 1+2+3+4
```

### Remove stuff

#### [`array.shift()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/shift) / [`array.pop()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/shift)

Remove first / last element of an array and store it

```javascript
let array = [1, 2, 3, 4];
let firstElement = array.shift(); // 1
let lastElement = array.pop(); // 4
console.log(array); // [2,3]
```

#### [`array.slice()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/slice)

Return new array with portion of initial array

```javascript
let array = [1, 2, 3, 4];
let arraySliced_1 = array.slice(1, 3); // [2,3]
let arraySliced_2 = array.slice(1, -1); // [2,3]
```

#### [`array.filter()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)

Create new array with all elements that pass the test (the function in argument)

```javascript
let array1 = [1, 2, 3];
let arrayFilterd = array1.filter((element) => element < 3); // [1, 2]
```

### Do operation on stuff

#### [`array.find()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find) / [`array.findIndex()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex)

Find elements and return the first one.

```javascript
let array = [1, 2, 3];
let elementFound = array.find((element) => element > 2); // 3
let indexFound = array.findIndex((element) => element > 2); // 2 (index of 3)
```

_If not find: `find()` will return `undefined`, and `findIndex()` will return `-1`._

#### [`array.sort()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)

Sort elements of an array and return the sorted array. Take a facultative comparaison function, which handle two arguments: the first element of the array compared with the second one

```javascript
let array = [3, 2, 1];
array.sort(); // [1,2,3]
array.sort((firstEl, secondEl) => secondEl - firstEl); // [3,2,1]
```

#### [`array.map()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)

Run a given function on each item of an array

```javascript
let array1 = [1, 2, 3];
let array2 = array1.map((element) => element * 2); // [2, 4, 6]
```

You can also define an object

```javascript
let array1 = ["a", "b", "c"];
let array2 = array.map((element, index) => ({ [index]: element })); // [{0:a} {1:b} {2:c}]
```

#### [`array.reduce()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce) / [`array.reduceRight()`](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global_Objects/Array/ReduceRight)

Run a given function on each element and keep it through an accumulator, resulting in a single output value. Can optionaly define the initial value to start with

```javascript
let array1 = [1, 2, 3];
const sum = array1.reduce((acc, curr) => acc + curr); // 6
const sum2 = array1.reduce((acc, curr) => acc + curr, 4); // 10
```

![](images/reduce.png)
