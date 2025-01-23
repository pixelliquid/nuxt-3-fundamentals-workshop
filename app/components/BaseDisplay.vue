<script setup>
import { computed, defineEmits, defineProps, ref } from 'vue'
import { useRoute } from 'vue-router' // composable = util function with composition API attached to it

const props = defineProps({
  itemList: {
    type: Array,
    default: () => [] // every instance will have its own array
    // default: [] // every instance will share the same array
  },
  title: {
    type: String,
    default: 'Default display title'
  }
})

const numberOfItems = computed(() => {
  return itemList.value.length
})

const emit = defineEmits(['update:itemList'])

// useRoute for dynamic route params
const route = useRoute()
// console.log(route.path) // result: /display/todos or /display/photos
const itemType = route.path.split('/')[2] // use the last bit in the path which is the name of the file within the display folder

// onMounted(() => { // lifeCycle hook which is triggered when the component is mounted, just fetch() ... in setup block works as well
function fetchData() { // function which is triggered by a click on the appropriate button
  fetch(`https://jsonplaceholder.typicode.com/${itemType}`)
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
      <slot name="items" :itemList="itemList" />
    </ul>
  </div>
</template>

<style></style>
