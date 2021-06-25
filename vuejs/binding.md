# [Binding](https://v3.vuejs.org/guide/forms.html)

## Two-way binding

Two-way binding is a simple way to link the value from the getter and the setter.

```html
<template>
	<input :value="msg" @input="updateMsg = $event.target.value" />
	{{ msg }}
</template>

<script>
	import { ref, computed } from "vue";
	export default {
		setup() {
			const msg = ref("hello");
			const updateMsg = computed({
				get: () => msg.value,
				set: val => (msg.value = val),
			});
			return { msg, updateMsg };
		},
	};
</script>
```

_`@input="searchText = $event.target.value"` call the setter method `set()`_

_`:value="searchText"` call the getter method `get()`_

### [`v-model`](https://v3.vuejs.org/guide/migration/v-model.html)

_Shorthand for two-way binding value._

```html
<template>
	<input v-model="msg" />
	{{ msg }}
</template>

<script>
	import { ref } from "vue";
	export default {
		setup() {
			const msg = ref("hello");
			return { msg };
		},
	};
</script>
```
