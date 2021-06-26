# [Components](https://v3.vuejs.org/guide/component-basics.html)

_Inside a component, directives notation change:_

- Prop `value` become `modelValue`
- Event `input` become `update:modelValue`

## Initialisation

```html
<template>
  <input-text />
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

## [Emit](https://v3.vuejs.org/guide/migration/emits-option.html#overview)

Emit events. Allow a parent component to get data from a child component.

```html
<!-- Parent component -->
<template>
  <input-text :value="outputValue" v-model="outputValue" />
  {{ outputValue }}
</template>

<script>
  import { ref } from "vue";
  import InputText from "./InputText.vue";

  export default {
    components: { InputText },
    setup() {
      const outputValue = ref("");
      return { outputValue };
    },
  };
</script>
```

```html
<!-- Child component -->
<template>
  <input type="text" v-model="inputValue" />
</template>

<script>
  import { computed } from "vue";

  export default {
    props: {
      value: { String },
    },
    setup(props, context) {
      const inputValue = computed({
        get: () => props.value,
        set: (val) => context.emit("update:value", val),
      });
      return { inputValue };
    },
  };
</script>
```

_Note: In component, `v-model="outputValue"` become the shorthand for `:modelValue="outputValue" @update:modelValue="outputValue = $event"`_
