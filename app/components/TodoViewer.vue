<script setup>
import { defineProps, ref, computed } from 'vue'

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

</script>

<template>
  <BaseDisplay title="Todo Viewer" itemType="todos" v-model:itemList="todoList">
    <template v-slot:hero> </template>

    <template v-slot:metrics>
      {{ completedItems.length }} completed |
      {{ remainingItems.length }} remaining
    </template>

    <template v-slot:items :completed="completedItems" :remaining="remainingItems">
    </template>
  </BaseDisplay>
</template>

<style lang="scss"></style>
