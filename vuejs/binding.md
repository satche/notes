# [Binding](https://v3.vuejs.org/guide/forms.html)

## Two-way binding

```html
<template>
	<input :value="msg" @input="msg = $event.target.value" />
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

**Shorthand**

```html
<input v-model="msg" />
<!-- …is the shorthand for: -->
<input :value="msg" @input="msg = $event.target.value" />
```

Do operation with `computed()`

```html
<template>
	<input v-model="msg" />
	{{ detailMsg }}
</template>

<script>
	import { ref, computed } from "vue";
	export default {
		setup() {
			const msg = ref("hello");
			const detailMsg = computed(() => "message: " + msg.value);
			return { msg, detailMsg };
		},
	};
</script>
```

_`@input="searchText = $event.target.value"` call the setter method `set()`_

_`:value="searchText"` call the getter method `get()`_
