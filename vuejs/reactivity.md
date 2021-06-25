# [Reactivity](https://v3.vuejs.org/guide/reactivity.html#what-is-reactivity)

## [`ref()`](https://v3.vuejs.org/guide/composition-api-introduction.html#reactive-variables-with-ref)

Reference. Encapsulate primitive in an object. Allows to track changes. Value given to the ref shouldn't be redefined (use of `const`)

```javascript
const a = ref(1);
console.log(a.value); // 1
```

## [`computed()`](https://v3.vuejs.org/guide/reactivity-computed-watchers.html#computed-values)

Allow to calculate reactive propreties (`ref()` object)

```javascript
const a = ref(1);
const b = computed(() => a.value + 2);
console.log(b.value); // 3
a.value = 3;
console.log(b.value); // 5
```

_Note: Computed properties are cached based on their reactive dependencies. Operations in template or in methods will be re-run everytime a re-render happens, even if the output is still the same. [Learn more](https://v3.vuejs.org/guide/computed.html#computed-caching-vs-methods)_

Define getter and setter for more control of the data.

```javascript
computed({
	get: () => a.value + 2,
	set: val => (a.value = val),
});
```

## [`watch()`](https://v3.vuejs.org/guide/reactivity-computed-watchers.html#watch) / [`watchEffect()`](https://v3.vuejs.org/guide/reactivity-computed-watchers.html#watcheffect)

Watch changes on reactive propreties (`ref()` object) and runs a given function right after.

```javascript
const a = ref(1);
watchEffect(() => console.log(a.value));
a.value = 2;
a.value = 3;
// 1
// 3
```

Use `watch()` to be more specific and handle old value

```javascript
const a = ref(1);
watch(a, (newValue, oldValue) => console.log(`${oldValue} => ${newValue}`));
a.value = 2;
a.value = 3;
// 1 => 3
```

_Note: `watch()` handle side effect lazily. That means, if value end to be the same at the end of the execution, nothing is run. On the other hand, `watchEffect()` will re-run the function even if value stay the same_
