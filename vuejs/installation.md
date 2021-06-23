# [Installation](https://v3.vuejs.org/guide/installation.html#release-notes)

## CDN / Self hosting

```html
<script src="https://unpkg.com/vue@next"></script>
```

## NPM + Webpack

```shell
$ npm install vue@next vue-loader@next @vue/compiler-sfc -D
```

`webpack.config.js`

```javascript
const webpack = require("webpack");
// …
module: {
	rules: [
		{
			test: /\.vue$/,
			loader: "vue-loader"
		}
	]
},
plugins: [
	new VueLoaderPlugin(),
]
// …
```

## [Vite](https://github.com/vitejs/vite)

```shell
$ npm init @vitejs/app <project-name>
$ cd <project-name>
$ npm install
$ npm run dev
```

# [Initalisation](https://v3.vuejs.org/guide/introduction.html#what-is-vue-js)

**Quick Hello World**

`index.js`

```javascript
import { createApp } from "vue";
import Component from "HelloWorld.vue";
const app = createApp(Component).mount("#app");
```

`HelloWorld.vue`

```html
<template> {{ msg }} </template>
<script>
	export default {
		setup() {
			const msg = "hello";
			return { msg };
		},
	};
</script>
```
