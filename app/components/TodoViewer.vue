<script setup>
import { defineProps, ref, computed } from 'vue'
// import Base from './Base.vue' - Nuxt infers this import from the component name

defineProps({
  title: {
    type: String,
    default: 'Hello Frontend Masters!'
  }
})

const todoList = ref([])

const completedItems = computed(() => {
  return todoList.value.filter(item => item.completed)
})

const remainingItems = computed(() => {
  return todoList.value.filter(item => !item.completed)
})

function fetchTodoList() {
  fetch('https://jsonplaceholder.typicode.com/todos/')
    .then(response => response.json())
    .then(json => {
      todoList.value = json
    })
}

const textModel = ref('')
</script>

<template>
  <Base scope="todos" title="Todo Viewer" v-model:itemList="todoList">
  <template v-slot:metrics>
    <pre>{{ todoList.length }} items | {{ completedItems.length }} items completed | {{ remainingItems.length }}
    remaining</pre>
    <pre>{{ todoList }}</pre>
  </template>
  <template v-slot:items="slotProps">
    <!--<pre>{{ slotProps.itemList }}</pre> -->
  </template>
  </Base>
</template>

<style lang="scss"></style>