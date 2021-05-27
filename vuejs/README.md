# [VueJS](https://v3.vuejs.org/)

_A set of VueJS notes, tips, tricks and general cheatsheet_

**Version:** 3.x

**Links**

- [Website Vue3](https://v3.vuejs.org/)
- [Repo github](https://github.com/vuejs/vue-next)

## Table of content

- [Installation / getting started](#init.md)

## TMP (to sort)

### [Reactivity](https://v3.vuejs.org/guide/reactivity.html#what-is-reactivity)

`ref()`
Wrap primitives in an object. Allows to track changes.

`computed()`
Allow to calculate propreties that depends on other propreties.

```javascript
let a = ref(1);
console.log(a.value); // 1

let b = computed(() => a.value + 2);
console.log(b.value); // 3

a = ref(3);
console.log(b.value); // 5
```

_Define getter and setter_

```javascript
computed({
	get: () => a.value + 2,
	set: val => a.value = val,
});
```

## TODO

@input="a = $event.target.value" // le "=" appelle le setter

changer get() + set() --> to-way-binding --> v-model

props() --> permet de définir des spécifitiés aux propriétés vue

ex.
props: {
label: { type: String, required: true }
}

setup(props, context)

option API vs. composition API

watch vs. watchEffect

https://www.vuemastery.com/pdf/Vue-3-Cheat-Sheet.pdf
https://learnvue.co/wp-content/uploads/2021/01/A-VueJS-Cheatsheet-for-Developers-__-By-LearnVue.co_.pdf
