<script>
import { defineNuxtComponent } from '#app' // helpful when using options API

export default defineNuxtComponent({
  data: () => ({
    photoGallery: []
  }),
  methods: {
    fetchPhotoGallery() {
      fetch('https://jsonplaceholder.typicode.com/photos/')
        .then(response => response.json())
        .then(json => {
          this.photoGallery = json
        })
      // same as above
      // .then(response => {
      //   this.photoGallery = response.json()
      // })
    }
  }
})
</script>

<template>
  <h1>Photo Gallery</h1>
  <button @click="fetchPhotoGallery">Fetch Photos</button>
  <ul>
    <li v-for="photo in photoGallery.slice(0, 20)" :key="`photo-id-${photo.id}`">
      <img :src="photo.thumbnailUrl" :alt="`${photo.title}`" />
    </li>
  </ul>
  <pre>{{ photoGallery }}</pre>
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