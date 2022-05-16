---
theme: ./theme
background: https://source.unsplash.com/collection/94734566/1920x1080
class: text-center
highlighter: shiki
lineNumbers: false
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
drawings:
  persist: false
title: Welcome to Slidev
---

# <span class="text-[#ffd700]">Interactive web apps with Vue</span>

Wisemen

---

# Korte inhoud


- **Tools** - Welke tools gaan we gebruiken
- **Project setup** - Hoe een project op te zetten
- **Folder structure** -  Folder structuur van een project
- **Vue syntax** - Hoe ziet een Vue file eruit
- **Nuttige packages** - Hoe ziet een Vue file eruit
- **Tailwind / windicss** - Hoe werkt tailwind
- **Wat gaan we maken** - Wat is het doel van deze les
- **API uitleg** - Hoe werkt de API die we gaan gebruiken

---
layout: image-right
image: https://miro.medium.com/max/1400/0*W06-5WbBC9aEKDVT
---

# Tools

## Visual studio code

<br/>

### Plugins

<br/>

- **Volar** - Fast Vue Language Support Extension
- **ESLint** - Code formatter / Regels
- **WindiCSS IntelliSense** - IntelliSense voor WindiCSS

---
layout: image-right
image: https://source.unsplash.com/collection/94734566/1920x1080
---

# Project Setup

[Vue Docs](https://vuejs.org/guide/quick-start.html#with-build-tools)

Simpele tutorial

### Skeleton project
[https://github.com/Robbe95/vue-skeleton](https://github.com/Robbe95/vue-skeleton)

```cmd {1|2|3|all}
npx degit Robbe95/vue-skeleton my-project-name
cd my-project-name
npm i
```

---

# Project structure

- **Assets** - Alle images / icons / assets
- **Components** - Vue components
- **Composables** -  Reusable Vue code snippets
- **Layouts** - Layouts van verschillende pagina's
- **Locales** - I18n files / Vertalingen
- **Pages** - Vue pagina's
- **Router** - Router files
- **Services** - API calls
- **Stores** - State managment
- **Types** - Typescript types

---
class: px-20
---

# Vue Syntax

### SFC - Single file components

- **Script** - Javascript / Typescript
- **Template** - HTML met Vue directives
- **Style** - CSS

```javascript
<script setup>
import { ref, onMounted } from 'vue'
const input = ref(null)

onMounted(() => {
  input.value.focus()
})
</script>

<template>
  <input ref="input" />
</template>

<style scoped>
</style>
```


---

# Script

## Composition API

```javascript
<script setup>
</script>
```

## Options API
```javascript
export default {
  data() {
    return {
      name: 'John',
    };
  },
  methods: {
    doIt() {
      console.log(`Hello ${this.name}`);
    },
  },
  mounted() {
    this.doIt();
  },
};
```

---

# Component

## Defining

```html
<script setup>
import { ref } from 'vue'

const count = ref(0)
</script>

<template>
  <button @click='count++'>
</template>
```

## Usage

```javascript
<script setup>
import ButtonCounter from './ButtonCounter.vue'
</script>

<template>
  <h1>Here is a child component!</h1>
  <ButtonCounter />
</template>
```

---

# Composition API

### Ref

```javascript
const count = ref(0)

console.log(count) // { value: 0 }
console.log(count.value) // 0

count.value++
console.log(count.value) // 1
```

---

# Composition API
### Computed
```javascript
import { ref, computed } from 'vue'

const author = ref({
  name: 'John Doe',
  books: [
    'Vue 2 - Advanced Guide',
    'Vue 3 - Basic Guide',
    'Vue 4 - The Mystery'
  ]
})

// a computed ref
const publishedBooksMessage = computed(() => {
  return author.books.length > 0 ? 'Yes' : 'No'
})


```
---

# Composition API
## Lifecycle hooks

### Before mounted

```javascript
import { onBeforeMounted } from 'vue'

onBeforeMounted(() => {
  console.log(`before mounted.`)
})
```
### Mounted

```javascript
import { onMounted } from 'vue'

onMounted(() => {
  console.log(`the component is now mounted.`)
})
```


---

# Composition API
## Lifecycle hooks

### Before update

```javascript
import { onBeforeUpdated } from 'vue'

onBeforeUpdated(() => {
  console.log(`before mounted.`)
})
```
### Update

```javascript
import { onUpdated } from 'vue'

onUpdated(() => {
  console.log(`the component is now mounted.`)
})
```

---

# Composition API
## Lifecycle hooks

### Before unmounted

```javascript
import { onBeforeUnmounted } from 'vue'

onBeforeUnmounted(() => {
  console.log(`before unmounted.`)
})
```
### Unmounted

```javascript
import { onUnmounted } from 'vue'

onUnmounted(() => {
  console.log(`the component is now unmounted.`)
})
```

---

# Composition API
## Watchers

```javascript
import { ref, watch } from 'vue'

const counter = ref(0)

watch(
  () => counter.value),
  () => {
    console.log('counter changed')
  },
)
```

---

# Composition API
## Props

```javascript
const props = defineProps(['foo'])

console.log(props.foo)
```

---

---

# Composition API
## Events

### Define
```javascript
const emits = defineEmits(['foo'])

const emitFoo = () => {
  emits('foo', extraData)
}

```

### Usage
```html
<MyComponent @foo="callback" />

<script setup>
  const callback = (data) => {
    console.log(data)
  }
</script>

```
---

# Template
## Class en style bindings

```html
<div
  class="static"
  :class="{ active: isActive, 'text-danger': hasError }"
></div>

<div :class="[isError ? 'bg-red-500' : 'bg-green-500']"></div>

<div :style="{ 'font-size': fontSize + 'px' }"></div>

```

---

# Template
## Conditional rendering

### V-if
```html
<h1 v-if="awesome">Vue is awesome!</h1>
<div v-else-if="otherCondiation">Test</div>
<h1 v-else>Oh no 😢</h1>

```

### V-show
```html
<h1 v-show="ok">Hello!</h1>
```

---

# Template
## List rendering

### V-for
```html
<script setup>
  const items = ref([{ message: 'Foo' }, { message: 'Bar' }])
</script>

<template>
  <li v-for="item in items" :key="item.message">
    {{ item.message }}
  </li>
  <span v-for="n in 10">{{ n }}</span>
</template>
```

---

# Template
## Event handeling

### V-for
```html
<script setup>
  const count = ref(0)
</script>

<template>
  <button @click="count++">Add 1</button>
  <p>Count is: {{ count }}</p>
</template>
```
---

# Template
## Event handeling

### Modifiers

```html
<!-- the click event's propagation will be stopped -->
<a @click.stop="doThis"></a>

<!-- the submit event will no longer reload the page -->
<form @submit.prevent="onSubmit"></form>

<!-- modifiers can be chained -->
<a @click.stop.prevent="doThat"></a>

<!-- just the modifier -->
<form @submit.prevent></form>

<!-- the click event will be triggered at most once -->
<a @click.once="doThis"></a>

<input @keyup.enter="submit" />
```

--- 

# Template
## Form input bindings

### Modifiers

```html
<p>Message is: {{ message }}</p>
<input v-model="message" placeholder="edit me" />
```

--- 

# Template
## Form input bindings

### Modifiers

```html
<p>Message is: {{ message }}</p>
<input v-model="message" placeholder="edit me" />
```

---

# Composition API
## Slots

### Define
```html
<button class="fancy-btn">
  <slot></slot> <!-- slot outlet -->
</button>

```

### Usage
```html
<FancyButton>
  Click me! <!-- slot content -->
</FancyButton>
```
---

# Style
## Scoped

```html
<style scoped>
.class {
  background-color: '#FFFFFF'
}
</style>
```

---

# Composables

## Define

```javascript
// mouse.js
import { ref, onMounted, onUnmounted } from 'vue'

// by convention, composable function names start with "use"
export function useMouse() {
  // state encapsulated and managed by the composable
  const x = ref(0)
  const y = ref(0)

  // a composable can update its managed state over time.
  function update(event) {
    x.value = event.pageX
    y.value = event.pageY
  }

  // a composable can also hook into its owner component's
  // lifecycle to setup and teardown side effects.
  onMounted(() => window.addEventListener('mousemove', update))
  onUnmounted(() => window.removeEventListener('mousemove', update))

  // expose managed state as return value
  return { x, y }
}
```

---

# Composables

## Usage

```html
<script setup>
import { useMouse } from './mouse.js'

const { x, y } = useMouse()
</script>

<template>Mouse position is at: {{ x }}, {{ y }}</template>
```


---

# Router

## Define
```javascript
import Home from '@/pages/Home.vue'
import About from '@/pages/About.vue'

const routes = [
  { path: '/', component: Home },
  { path: '/details', component: About },
]

const router = VueRouter.createRouter({
  history: VueRouter.createWebHistory(),
  routes,
})

const app = Vue.createApp({})
app.use(router)

app.mount('#app')
```
---

# Router
## Usage

```html
<template>
  <router-link to="/">Go to Home</router-link>
  <router-link to="/about">Go to About</router-link>
</template>
```

```javascript
import { useRouter } from 'router'
const router = useRouter()

router.push('/login')


```

---


# WindiCSS

## Cheat sheet
[Cheat sheet](https://nerdcave.com/tailwind-cheat-sheet)

## Examples

```html
<div class="bg-green-500"></div>
<div class="bg-green-500/50"></div>
<div class="bg-[#FFFFFF]"></div>
<div class="h-full"></div>
<div class="h-8"></div>
<div class="flex flex-row gap-2"></div>
<div class="md:bg-green-500 bg-red-500"></div>
<div class="transition hover:bg-red-500 bg-green-500 duration-400"></div>

```

---



