# [Components](https://v3.vuejs.org/guide/component-basics.html)

## Initialisation

```html
<template>
	<input-text></input-text>
</template>

<script>
	import InputText from "./components/InputText.vue";

	export default {
		components: { InputText },
	};
</script>
```

## [Props](https://v3.vuejs.org/guide/component-props.html)

Component proprieties. Allow the parent component/element to parse data to child components.

```html
<template>
	<h1>{{ title }}</h1>
	<span>{{ msgTitle }}</span>
</template>

<script>
	export default {
		props: {
			title: { type: String },
		},
		setup(props) {
			const msgTitle = "Welcome to " + props.title;
			return { msgTitle };
		},
	};
</script>
```

Then pass the prop in parent component: `<component title='Homepage'></component>`

**WIP: provide/inject, allow to parse data to a grandchild component**

## [Emit](https://v3.vuejs.org/guide/migration/emits-option.html#overview)

Emit events. Allow a parent component to get data from a child component.

```html
<!-- Child component -->
<template>
	<input type="text" v-model="emitValue" />
</template>

<script>
	import { ref, computed } from "vue";

	export default {
		emits: ["update:value"],
		setup(props, context) {
			const inputValue = ref("");
			const emitValue = computed({
				get: () => inputValue.value,
				set: val => context.emit("update:value", val),
			});
			return { emitValue };
		},
	};
</script>
```

```html
<!-- Parent component -->
<template>
	<input-text @update:value="updateValue = $event"></input-text>
	{{ outputValue }}
</template>

<script>
	import { ref, computed } from "vue";
	import InputText from "./components/InputText.vue";

	export default {
		components: { InputText },
		setup() {
			const outputValue = ref("");
			const updateValue = computed({
				get: () => value.value,
				set: val => (value.value = val),
			});
			const log = event => console.log(event);
			return { log, outputValue, updateValue };
		},
	};
</script>
```
