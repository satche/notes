# [VueJS](https://v3.vuejs.org/)

_A set of VueJS notes, tips, tricks and general cheatsheet_

**Version:** 3.x

**Links**

- [Website Vue3](https://v3.vuejs.org/)
- [Repo github](https://github.com/vuejs/vue-next)

## Table of content

- [Installation / getting started](#installation.md)
- [Reactivity](#reactivity.md)
  - [`ref()`](<#reactivity.md#ref()>)

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
