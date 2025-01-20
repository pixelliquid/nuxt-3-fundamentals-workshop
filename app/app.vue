<script setup>
import { computed, ref } from 'vue'

let photoGallery = ref([])

const numberOfPhotos = computed(() => {
  return photoGallery.value.length
})

const evenAlbums = computed(() => {
  return photoGallery.value.filter(item => item.albumId % 2 === 0)
})

const oddAlbums = computed(() => {
  return photoGallery.value.filter(item => !(item.albumId % 2 === 0))
})

function fetchPhotoGallery() {
  fetch('https://jsonplaceholder.typicode.com/photos')
    .then(response => response.json())
    .then(json => {
      photoGallery.value = json
    })
}
</script>

<template>
  <div class="section">
    <h1 class="title">Photo Gallery</h1>
    <button @click="fetchPhotoGallery">Fetch Data</button>
    <p>
      {{ numberOfPhotos }} photos ({{ oddAlbums.length }} odd albums |
      {{ evenAlbums.length }} even albums)
    </p>
    <ul class="list">
      <li v-for="photo in photoGallery.slice(0, 20)" :key="`photo-id-${photo.id}`">
        <img :src="photo.thumbnailUrl" />
      </li>
    </ul>
  </div>
</template>

<style lang="scss">
@import './node_modules/bulma/bulma.sass';
@import './assets/styles/main.scss';
</style>
