<script setup lang="ts">
import { ref } from 'vue'

const msg = ref('Hello Vue 2.7!')
</script>

<template>
  <h1>{{ msg }}</h1>
  <input v-model="msg" />
</template>
