<script setup lang="ts">
defineProps({
  msg: String,
})

const emit = defineEmits(['response'])

emit('response', 'test emit!!!!!!!!!')
</script>

<template>
  <h2>ChildComponent</h2>
  <div>{{ msg === '' ? 'no message' : msg }}</div>
</template>
