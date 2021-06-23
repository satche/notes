# [Reactivity](https://v3.vuejs.org/guide/reactivity.html#what-is-reactivity)

## [`ref()`](https://v3.vuejs.org/guide/composition-api-introduction.html#reactive-variables-with-ref)

Reference. Encapsulate primitive in an object. Allows to track changes. Value given to the ref shouldn't be redefined (use of `const`)

```javascript
const a = ref(1);
console.log(a.value); // 1
```

## [`watch()`](https://v3.vuejs.org/guide/reactivity-computed-watchers.html#watch)

Watch changes on a reactive variable (`ref()` object)

```javascript
const a = ref(1);
watch(a, (newValue, oldValue) => console.log(`${oldValue} => ${newValue}`));
a.value = 2;
// 1 => 2
```

## [`computed()`](https://v3.vuejs.org/guide/reactivity-computed-watchers.html#computed-values)

Allow to calculate propreties that depends on other propreties.

```javascript
const a = ref(1);
const b = computed(() => a.value + 2);
console.log(b.value); // 3
a.value = 3;
console.log(b.value); // 5
```

Define getter and setter (WIP)

```javascript
computed({
	get: () => a.value + 2,
	set: val => (a.value = val),
});
```
