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

```javascript
props: {
   title: {
      type: String,
      required: true,
      default: "hello world"
   }
}
```

<details>

<summary>Quick example</summary>

```html
<!-- Parent component -->
<template>
   <component title="Homepage"></component>
   <component :title="content"></component>
</template>

<script>
   import Component from "./Component.vue";
   export default {
      components: {
         Component,
      },
      setup() {
         const content = "Hello world";
         return { content };
      },
   };
</script>
```

```html
<!-- Child component -->
<template>
   <h1>{{ title }}</h1>
   <span>{{ msgTitle }}</span>
</template>

<script>
   export default {
      props: ["title"],
      setup(props) {
         const msgTitle = "Welcome to " + props.title;
         return { msgTitle };
      },
   };
</script>
```

</details>

<details>

<summary>Pass object to props</summary>

```html
<!-- Parent component -->
<template>
   <post v-bind:title="post.title" v-bind:msg="post.msg"></post>
   <!-- shorthand: v-bind="post" -->
</template>

<script>
   import Post from "./Post.vue";
   export default {
      components: {
         Post,
      },
      setup() {
         const post = {
            title: "Hello",
            msg: "How are you ?",
         };
         return { post };
      },
   };
</script>
```

```html
<!-- Child component -->
<template>
   <h1>{{ title }}</h1>
   <p>{{ msg }}</p>
</template>

<script>
   export default {
      props: ["title", "msg"],
   };
</script>
```

</details>

<hr>

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
