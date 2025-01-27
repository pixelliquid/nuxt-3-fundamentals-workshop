<script setup>
import { NuxtLayout } from '#components'
import { computed, ref } from 'vue'
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
  <NuxtLayout name="todos">
    <div class="container">
      <NuxtPage v-if="route.params.id" />
      <BaseDisplay v-else title="Todo Viewer" v-model:itemList="todoList">
        <template v-slot:metrics>
          <pre>{{ todoList.length }} items | {{ completedItems.length }} items completed | {{ remainingItems.length }}
          remaining</pre>
          <!-- <pre>{{ todoList }}</pre> -->
        </template>
        <template v-slot:items>
          <li v-for="todo in filteredTodoList" :key="`todo-id-${todo.id}`">
            <input type="checkbox" :checked="todo.completed" />
            <NuxtLink :to="`/display/todos/${todo.id}`">{{ todo.title }}</NuxtLink>
          </li>
        </template>
      </BaseDisplay>
    </div>
  </NuxtLayout>
</template>

<style lang="scss"></style>
