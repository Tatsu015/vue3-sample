<script setup lang="ts">
const props = defineProps({
  msg: String,
})
</script>

<template>
  <h2>ChildComponent</h2>
  <div>{{ msg === '' ? 'no message' : msg }}</div>
</template>
