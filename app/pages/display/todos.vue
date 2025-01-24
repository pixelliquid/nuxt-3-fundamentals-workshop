<script setup>
import { ref, computed } from 'vue'
// import Base from './Base.vue' - Nuxt infers this import from the component name

const todoList = ref([])

const route = useRoute()
console.log(route.query.completed)

const completedItems = computed(() => {
  return todoList.value.filter(item => item.completed)
})

const remainingItems = computed(() => {
  return todoList.value.filter(item => !item.completed)
})

const filteredTodoList = computed(() => {
  switch (route.query.completed) {
    case 'true':
      return completedItems.value
    case 'false':
      return remainingItems.value
    default:
      return todoList.value
  }
})
</script>

<template>
  <div class="container">
    <BaseDisplay title="Todo Viewer" v-model:itemList="todoList">
      <template v-slot:metrics>
        <pre>{{ todoList.length }} items | {{ completedItems.length }} items completed | {{ remainingItems.length }}
        remaining</pre>
        <!-- <pre>{{ todoList }}</pre> -->
      </template>
      <template v-slot:items>
        <li v-for="todo in filteredTodoList" :key="`todo-id-${todo.id}`">
          <input type="checkbox" :checked="todo.completed" /> {{ todo.title }}
        </li>
      </template>
    </BaseDisplay>
  </div>
</template>

<style lang="scss"></style>
