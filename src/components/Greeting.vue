<script setup>
const props = defineProps({
  name: String
})
const emit = defineEmits(['response']);

emit('response', 'hello from child')

console.log(emit)
</script>

<template>
  <h1>Hello, {{ name || "There's Nothing here" }}</h1>
  <slot>
    fallback
  </slot>
</template>