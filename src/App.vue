<script setup lang="ts">
import { ref } from 'vue'

const count = ref(0)
const message = ref('count!!!')
const messageCssClass = ref('msg')
const increment = () => {
  count.value++
}
const reset = () => {
  count.value = 0
}
</script>

<template>
  <h1 :class="messageCssClass">{{ message }}</h1>
  <button @click="increment">CLICK ME!!!</button>
  <div>{{ count }}</div>
  <button @click="reset">reset</button>
</template>

<style>
.msg {
  color: red;
  font-size: xx-large;
}
</style>
