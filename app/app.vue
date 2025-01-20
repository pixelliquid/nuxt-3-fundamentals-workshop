<script>
import { defineNuxtComponent } from '#app' // helpful when using options API

export default defineNuxtComponent({
  data: () => ({
    photosList: []
  }),
  methods: {
    fetchPhotosList() {
      fetch('https://jsonplaceholder.typicode.com/photos/')
        .then(response => response.json())
        .then(json => {
          this.photosList = json
        })
    }
  }
})
</script>

<template>
  <h1>Photo Gallery</h1>
  <button @click="fetchPhotosList">Fetch Photos</button>
  <ul>
    <li v-for="photo in photosList.slice(0, 20)" :key="`photo-id-${photo.id}`">
      <img :src="photo.thumbnailUrl" :alt="`${photo.title}`" />
    </li>
  </ul>
  <pre>{{ photosList }}</pre>
</template>

<style>
  img {
    width: 100%;
  }
  ul {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
  }
</style>