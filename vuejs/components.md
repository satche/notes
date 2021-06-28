# [Components](https://v3.vuejs.org/guide/component-basics.html)

_Inside a component, directives notation change:_

-  Prop `value` become `modelValue`
-  Event `input` become `update:modelValue`

## [Initialisation](https://v3.vuejs.org/guide/component-basics.html)

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

## [Emit](https://v3.vuejs.org/guide/migration/emits-option.html#overview)

Emit events. Allow a parent component to get data from a child component.

<details>

<summary>Send value from child's input to parent</summary>

```html
<!-- Parent component -->
<template>
   <input-text
      :value="outputValue"
      @update:modelValue="outputValue = $event"
   ></input-text>
   <!-- shorthand: v-model="outputValue" -->
   {{ outputValue }}
</template>

<script>
   import { ref } from "vue";
   import InputText from "./InputSimple.vue";

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
   <input :value="modelValue" @input="modelValue = $event.target.value" />
   <!-- shorthand: v-model="modelValue" -->
</template>

<script>
   import { computed } from "vue";
   export default {
      props: ["modelValue"],
      emits: ["update:modelValue"],
      setup(props, context) {
         const modelValue = computed({
            get: () => props.modelValue,
            set: (val) => context.emit("update:modelValue", val),
         });
         return { modelValue };
      },
   };
</script>
```

</details>

<details>

<summary>Name custom event</summary>

```html
<!-- Parent component -->
<template>
   <input-text :label="outputValue" @update:label="outputValue = $event" />
   <!-- shorthand: v-model:label='outputValue' -->
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
   <input :value="label" @input="$emit('update:label', $event.target.value)" />
</template>

<script>
   export default {
      props: ["label"],
      emits: ["update:label"],
   };
</script>
```

</details>

<details>

<summary>Use emit in template (not best practice)</summary>

```html
<!-- Parent component -->
<template>
   <input-text @update:statut="statut = $event" />
   {{ statut }}
</template>

<script>
   import { ref } from "vue";
   import InputText from "./InputText.vue";

   export default {
      components: { InputText },
      setup() {
         const statut = ref("(nothing)");
         return { statut };
      },
   };
</script>
```

```html
<!-- Child component -->
<template>
   <input @input="$emit('update:statut', statut)" />
</template>

<script>
   export default {
      emits: ["update:statut"],
      setup() {
         const statut = "Triggerd";
         return { statut };
      },
   };
</script>
```

</details>

<hr>

## WIP

_Provide and Inject: allow to parse data to a grandchild component_
