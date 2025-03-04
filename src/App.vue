<script setup lang="ts">
import { ref, type Ref } from 'vue'

type Todo = {
  id: number
  text: string
}

const todo: Ref<string> = ref('')
const todos: Ref<Todo[]> = ref([{ id: Date.now(), text: 'lean html' }])

const handleDelete = (todo: Todo) => {
  console.log('delete', todo)
  todos.value = todos.value.filter((t) => t.id !== todo.id)
}

const handleAdd = () => {
  console.log('add', todo.value)
  todos.value.push({ id: Date.now(), text: todo.value })
}
</script>

<template>
  <input type="text" placeholder="new todo" v-model="todo" />
  <button @click="handleAdd">Add Text</button>

  <ul>
    <li v-for="item in todos" :key="item.id">
      {{ item.id }}{{ item.text }}
      <button @click="handleDelete(item)">X</button>
    </li>
  </ul>
</template>

<style></style>
