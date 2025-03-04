<script setup lang="ts">
import { ref } from 'vue'
import ChildComponent from './components/ChildComponent.vue'
const childMessage = ref('')
</script>
<template>
  <ChildComponent msg="test message" @response="(msg) => (childMessage = msg)" />
  <div>{{ childMessage }}</div>
</template>
