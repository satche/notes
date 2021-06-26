# [Reactivity](https://v3.vuejs.org/guide/reactivity.html#what-is-reactivity)

## [`ref()`](https://v3.vuejs.org/guide/composition-api-introduction.html#reactive-variables-with-ref)

<details>

<summary>Reactive propreties</summary>

**Usage**

```javascript
const a = ref(1);
console.log(a.value); // 1
```

**Good to know**

- Encapsulate primitive in an object to allow the reactivity.
- Value given to the ref shouldn't be redefined (use of `const`)

</details>

## [`computed()`](https://v3.vuejs.org/guide/reactivity-computed-watchers.html#computed-values)

<details>

<summary>Do operation on reactive propreties</summary>

**Usage**

```javascript
const a = ref(1);
const b = computed(() => a.value + 2);
console.log(b.value); // 3
```

**Shorthand**

```javascript
computed(() => a.value);
// … is the shortand for:
computed({
	get: () => a.value,
	set: val => (a.value = val),
});
```

**Good to know**

- Computed properties are cached based on their reactive dependencies. Operations in template or in methods will be re-run everytime a re-render happens, even if the output is still the same. [Learn more](https://v3.vuejs.org/guide/computed.html#computed-caching-vs-methods)\_

</details>

## [`watch()`](https://v3.vuejs.org/guide/reactivity-computed-watchers.html#watch) and [`watchEffect()`](https://v3.vuejs.org/guide/reactivity-computed-watchers.html#watcheffect)

<details>

<summary>Do operation when reactive properties change</summary>

**Usage**

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

**Good to know**

- `watch()` handle side effect lazily. That means, if value end to be the same at the end of the execution, nothing is run. On the other hand, `watchEffect()` will re-run the function even if value stay the same

</details>
