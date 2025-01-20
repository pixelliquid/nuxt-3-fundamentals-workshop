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
  return photoGallery.value.filter(item => item.albumId % 2 !== 0)
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
  <div>
    <img src="/todo.jpg" alt="Todo photo by Glenn Casterns-Peters" />
    <p>
      Photo by
      <a
        href="https://unsplash.com/@glenncarstenspeters?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Glenn
        Carstens-Peters</a>
      on
      <a
        href="https://unsplash.com/s/photos/todo?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>
    </p>
    <h1>Hello Frontend Masters!</h1>
    <button @click="fetchPhotoGallery">Fetch Photos</button>
    <ul>
      <li v-for="photo in photoGallery" :key="`photo-id-${photo.id}`">
        <img :src="photo.thumbnailUrl" :alt="photo.title" />
      </li>
    </ul>
  </div>
</template>
