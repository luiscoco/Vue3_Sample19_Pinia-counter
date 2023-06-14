# pinia-sample

Create a new project with Vue3. Open a windows terminal in VSCode and run the command:

vue create pinia-sample

Select the options, move with arrow keys and select with the space bar: Options selection summary:

```
Vue CLI v5.0.8
? Please pick a preset: Manually select features
? Check the features needed for your project: Babel, TS, Linter
? Choose a version of Vue.js that you want to start the project with 3.x
? Use class-style component syntax? No
? Use Babel alongside TypeScript (required for modern mode, auto-detected polyfills, transpiling JSX)? Yes
? Pick a linter / formatter config: Prettier
? Pick additional lint features: Lint on save
? Where do you prefer placing config for Babel, ESLint, etc.? In dedicated config files
? Save this as a preset for future projects? (y/N) n
```

In Vue 3, Pinia is a state management library that provides a reactive store pattern. It is designed to be used with the Composition API, which allows you to organize and reuse your code in a more functional manner. Pinia aims to be lightweight and scalable while leveraging the reactivity system of Vue 3.

To create a simple counter application using Pinia with the Composition API and TypeScript, you can follow these steps:

Install Pinia using npm or yarn:

npm install pinia

or

yarn add pinia

## main.ts

Open the main.ts file and add the necessary imports:

```typescript
import { createApp } from "vue";
import { createPinia } from "pinia";
import App from "./App.vue";

const app = createApp(App);
const pinia = createPinia();

app.use(pinia);
app.mount("#app");
```

## store.ts

Create a new file named counter.ts in the src/store directory:

```typescript
import { defineStore } from "pinia";

export const useCounterStore = defineStore("counter", {
  state: () => ({
    count: 0,
  }),
  actions: {
    increment() {
      this.count++;
    },
    decrement() {
      this.count--;
    },
  },
});
```

## App.vue

Create a new file named App.vue in the src directory:

```vue
<template>
  <div>
    <label>Counter: {{ counter.count }}</label>
  </div>
  <div>
    <button @click="increment">Increment</button>
    <button @click="decrement">Decrement</button>
  </div>
</template>

<script lang="ts" setup>
import { useCounterStore } from "../src/store/store";

const counter = useCounterStore();

function increment() {
  counter.increment();
}

function decrement() {
  counter.decrement();
}
</script>
```

In this example, we defined a store named "counter" using Pinia's defineStore function. It has a single state property called "count" initialized to 0 and two actions, "increment" and "decrement", which modify the count.

In the App.vue component, we imported the useCounterStore function from the counter.ts file and initialized the counter variable using it. We then defined two helper functions, increment and decrement, which call the respective actions on the counter store.

The counter value is displayed in the template using the double curly braces syntax ({{ counter }}), and the buttons trigger the corresponding actions when clicked.

That's a basic example of using Pinia with the Composition API in Vue 3 to create a simple counter application. You can expand on this foundation to build more complex applications with multiple stores and shared state.


## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
