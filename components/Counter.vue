<script setup lang="ts">
import { ref } from 'vue'

const props = defineProps({
  count: {
    default: 0
  }
})

const counter = ref(props.count)

const decrement = () => counter.value--
const increment = () => counter.value++
</script>

<template>
  <div flex="~" w="min" border="~ main rounded-md">
    <button
      border="r main"
      p="2"
      font="mono"
      outline="!none"
      hover:bg="gray-400 opacity-20"
      @click="decrement"
    >
      -
    </button>
    <span m="auto" p="2">{{ counter }}</span>
    <button
      border="l main"
      p="2"
      font="mono"
      outline="!none"
      hover:bg="gray-400 opacity-20"
      @click="increment"
    >
      +
    </button>
  </div>
</template>
