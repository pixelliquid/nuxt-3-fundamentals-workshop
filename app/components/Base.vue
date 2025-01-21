<script setup>
import { computed, defineProps, ref } from 'vue'

let itemList = ref([])

defineProps({
  title: {
    type: String,
    default: 'Hello Frontend Masters!'
  },
  scope: {
    type: String,
    default: 'todos'
  }
})

const numberOfItems = computed(() => {
  return itemList.value.length
})

function fetchData(sope) {
  fetch(`https://jsonplaceholder.typicode.com/${scope}`)
    .then(response => response.json())
    .then(json => {
      itemList.value = json
    })
}

</script>

<template>
  <div class="section">
    <h1 class="title">{{ title }}</h1>
    <button @click="fetchData">Fetch Data</button>
    <slot>
      <p>{{ numberOfItems }} items</p>
    </slot>
    <ul>
      <li v-for="item in itemList" :key="`item-${item.id}`">
        {{ item.title }}
      </li>
    </ul>
  </div>
</template>

<style lang="scss"></style>