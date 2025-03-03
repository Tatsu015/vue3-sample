<script setup lang="ts">
import { ref } from 'vue'

const message = ref('hello world')
const cls = ref('msg')
</script>

<template>
  <h1 :class="cls">{{ message }}</h1>
</template>

<style>
.msg {
  color: red;
}
</style>
