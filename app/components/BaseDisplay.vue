<script setup>
import { computed, defineEmits, defineProps, ref } from 'vue'

const props = defineProps({
  itemsList: {
    type: Array,
    default: () => []
  },
  scope: {
    type: String,
    default: 'todos'
  },
  title: {
    type: String,
    default: 'Default display title'
  }
})

const emit = defineEmits(['update:itemList'])

const numberOfItems = computed(() => {
  return itemList.value.length
})

function fetchData() {
  fetch(`https://jsonplaceholder.typicode.com/${props.scope}`)
    .then(response => response.json())
    .then(json => {
      emit('update:itemList', json)
    })
}

function clearData() {
  emit('update:itemList', [])
}

</script>

<template>
  <div class="section">
    <h1 class="title">{{ title }}</h1>
    <button @click="fetchData">Fetch Data</button>
    <button @click="clearData">Clear Data</button>
    <slot name="metrics" />
    <ul>
      <!-- replace li for slot -->
      <slot name="items" :itemList="itemList" />
      <!-- <li v-for="item in itemList" :key="`item-${item.id}`">
        {{ item.title }}
      </li> -->
    </ul>
  </div>
</template>

<style lang="scss"></style>