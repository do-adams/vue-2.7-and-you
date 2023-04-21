---
# try also 'default' to start simple
theme: vuetiful
# apply any windi css classes to the current slide
class: 'text-center'
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: false
# persist drawings in exports and build
drawings:
  persist: false
# page transition
transition: slide-left
# use UnoCSS
css: unocss
---

# Vue 2.7 and You

What You Need to Know

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
transition: fade-out
---

# What is Vue 2.7?

Vue 2.7 is an upgrade that brings several major features from Vue 3 to Vue 2.

- Released on July 1, 2022
- Brings native support for the Composition API
- Brings support for `<script setup>` in SFCs
- Brings support for CSS `v-bind` in SFCs
- Improves type inference for `defineComponent()` in SFCs
- Adds type checking for `emits` in SFCs
- Adds new `eslint-plugin-vue` rules for catching bugs with the Composition API
- Uses Volar instead of Vetur for IDE integration

<br>

Read more about [Vue 2.7](https://blog.vuejs.org/posts/vue-2-7-naruto)

---

# What's new? Composition API

```vue
<script>
import { ref, defineComponent } from 'vue'

export default defineComponent({
  setup() {
    const msg = ref('Hello World!')
    return {
      msg
    }
  }
})
</script>

<template>
  <h1>{{ msg }}</h1>
  <input v-model="msg" />
</template>

```

No more `import { ref, defineComponent } from '@vue/composition-api'`

---

# What's new? `<script setup>`

```vue
<script setup lang="ts">
import { ref } from 'vue'

const msg = ref('Hello from <script setup> 👋')
</script>

<template>
  <div>
    <h1>{{ msg }}</h1>
    <input v-model="msg" />
  </div>
</template>

```

Unfortunately cannot be used in our codebase until we upgrade to Vite and Vitest.

---

# What's new? CSS `v-bind`

We can now easily link CSS values to component state with the new `v-bind` CSS function.

```vue
<template>
  <div class="text">hello</div>
</template>

<script lang="ts">
export default {
  data() {
    return {
      color: 'red'
    }
  }
}
</script>

<style>
.text {
  color: v-bind(color);
}
</style>

```

---

# What's new? `getCurrentInstance()`

```vue
<script lang="ts">
import { defineComponent, getCurrentInstance } from 'vue';

export default defineComponent({
  // ...
  setup(props, context) {
    const vm = getCurrentInstance()
    const { $gettext, $language, $userEvents, $vuetify } = vm?.proxy as Vue

    // ...
  }
})
```

---

# What's new? Router Composables

```vue
<script lang="ts">
import { useRoute, useRouter } from 'vue-router/composables';

export default defineComponent({
  // ...
  setup(props, context) {
    const $router = useRouter()
    const $route = useRoute()

    // ...
  }
})
```

---

# What's new? Volar

Volar is the official VSCode extension that provides TypeScript support inside Vue SFCs, along with many other great features.

Volar replaces Vetur, our previous official VSCode extension for Vue 2. If you have Vetur currently installed, make sure to disable it in Vue 3 projects.

Read more about how to set up [Volar](https://vuejs.org/guide/typescript/overview.html#volar-takeover-mode).

---
layout: center
---

# Bonus - VueUse

---

<iframe src="https://vueuse.org/core/useMouse/#usemouse" style="width: 100%; height: 100%;"></iframe>

---

<iframe src="https://vueuse.org/core/useRefHistory/#userefhistory" style="width: 100%; height: 100%;"></iframe>

---

<iframe src="https://vueuse.org/shared/refDebounced/#refdebounced" style="width: 100%; height: 100%;"></iframe>

---

<iframe src="https://vueuse.org/core/useAsyncState/#useasyncstate" style="width: 100%; height: 100%;"></iframe>

