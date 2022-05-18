# Vue 3 + Vite

This template should help get you started developing with Vue 3 in Vite. The template uses Vue 3 `<script setup>` SFCs, check out the [script setup docs](https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup) to learn more.

## Recommended IDE Setup

- [VS Code](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=johnsoncodehk.volar)

## TailwindCSS

Tailwind CSS JIT installed along with PostCSS and autoprefixer

## Steps for reproduction

1. New Vite Vue 3 app
  - `npm create vite@latest app-name --template vue`
  - `npm i`
2. Vue Router
  - `npm i vue-router@4`
  - create a new router (`./src/router.js`)

```js
// ./src/router.js
import { createRouter, createWebHistory } from "vue-router"

const routes = [
  {
    path: "/",
    name: "Home",
    component: _ => import("./components/Home.vue")
  },
]

const router = createRouter({
  history: createWebHistory(),
  routes,
})

export default router
```

  - include `<router-view />`

```html
<!-- App.vue -->
<template>
  <router-view />
</template>
```

  - mount the router

```js
import { createApp } from "vue"
import App from "./App.vue"
import router from "./router.js"
import "index.css"

createApp(App).use(router).mount("#app")
```

4. TailwindCSS (JIT)
  - `npm i -D tailwindcss postcss autoprefixer`
  - `npx tailwindcss init -p`
  - Configure - edit `tailwind.config.js`

```js
// tailwind.config.js
module.exports = {
    content: [
        "./index.html",
        "./src/**/*.{vue,js}",
    ],
    theme: {
        extend: {},
    },
    plugins: [],
}
```

  - Use Tailwind directives in your CSS (for example `./src/index.css`)

```css
/* ./src/index.css */
@tailwind base;
@tailwind components;
@tailwind utilities;
```

```js
import { createApp } from "vue"
import App from "./App.vue"
import "index.css"

createApp(App).mount("#app")
```
