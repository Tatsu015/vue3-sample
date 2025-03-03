<script setup lang="ts">
import { ref } from 'vue'

const count = ref(0)
const message = ref('count!!!')
const messageCssClass = ref('msg')
const visible = ref(false)

const increment = () => {
  count.value++
}
const reset = () => {
  count.value = 0
}
const toggle = () => {
  visible.value = !visible.value
}
</script>

<template>
  <h1 :class="messageCssClass">{{ message }}</h1>
  <button @click="increment">CLICK ME!!!</button>
  <div>{{ count }}</div>
  <button @click="reset">reset</button>

  <input v-model="message" />

  <button @click="toggle">toggle</button>
  <div v-if="visible">Visible!!</div>
  <div v-else>Unvisible...</div>
  <div>{{ visible ? 'Visible' : 'Unvisible' }}</div>

  <!-- this format not OK because *.vue not tsx -->
  <!-- <div>{{ visible? <div>Visible</div>:<div>Unvisible</div> }}</div> -->
</template>

<style>
.msg {
  color: red;
  font-size: xx-large;
}
</style>
