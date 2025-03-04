<script setup lang="ts">
import { computed, ref, type Ref } from 'vue'

let count = 0

type Todo = {
  id: number
  text: string
  done: boolean
}

const todo: Ref<string> = ref('')
const todos: Ref<Todo[]> = ref([
  { id: count++, text: 'lean html', done: false },
  { id: count++, text: 'lean js', done: false },
  { id: count++, text: 'lean css', done: false },
])
const hideCompleted = ref(false)

const handleDelete = (todo: Todo) => {
  console.log('delete', todo)
  todos.value = todos.value.filter((t) => t.id !== todo.id)
}

const handleAdd = () => {
  console.log('add', todo.value)
  todos.value.push({ id: count++, text: todo.value, done: false })
}

const handleHideCompleted = () => {
  hideCompleted.value = !hideCompleted.value
}

const filteredTodos = computed(() => {
  return hideCompleted.value ? todos.value.filter((t) => t.done !== true) : todos.value
})
</script>

<template>
  <input type="text" placeholder="new todo" v-model="todo" />
  <button @click="handleAdd">Add Text</button>
  <div></div>
  <button @click="handleHideCompleted">
    {{ hideCompleted ? 'Show completed' : 'Hide completed' }}
  </button>
  <ul>
    <li v-for="item in filteredTodos" :key="item.id">
      <input type="checkbox" v-model="item.done" />
      <span :class="{ done: item.done }">
        {{ item.text }}
      </span>
      <button @click="handleDelete(item)">X</button>
    </li>
  </ul>
</template>

<style>
.done {
  text-decoration: line-through;
}
</style>
