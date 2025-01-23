<script setup>
import { ref, computed } from 'vue'

const todoList = ref([])

// const filteredTodoList = computed(() => {
//   if (route.query.completed) {
//     return completedItems.value
//   } else {
//     return remainingItems.value
//   }
// })

const completedItems = computed(() => {
  return todoList.value.filter(item => item.completed)
})

const remainingItems = computed(() => {
  return todoList.value.filter(item => !item.completed)
})
</script>

<template>
  <div class="container">
    <BaseDisplay :itemType="itemType" title="Todo Viewer" v-model:itemList="todoList">
    <template v-slot:metrics>
      <pre>{{ todoList.length }} items | {{ completedItems.length }} items completed | {{ remainingItems.length }} remaining</pre>
      <pre>{{ todoList }}</pre>
    </template>
    <template v-slot:items>
      <li v-for="todo in todoList" :key="`todo-id-${todo.id}`">
        <input type="checkbox" :checked="todo.completed" /> {{ todo.title }}
      </li>
      <!-- <li v-for="todo in filteredTodoList" :key="`todo-id-${todo.id}`">
        <input type="checkbox" :checked="todo.completed" /> {{ todo.title }}
      </li> -->
    </template>
    </BaseDisplay>
  </div>
</template>

<style lang="scss"></style>
