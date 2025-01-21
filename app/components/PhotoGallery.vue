<script setup>
import { computed, ref } from 'vue'
import Base from './Base.vue'

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
  <Base scope="photos" title="Photo Galley" v-model:itemList="photoGallery">
  <template v-slot:metrics>
    <pre>{{ numberOfPhotos }} photos in {{ evenAlbums.length }} even albums and {{ oddAlbums.length }} odd albums</pre>
    <pre>{{ photoGallery }}</pre>
  </template>
  <template v-slot:items>
    <ul>
      <li v-for="photo in photoGallery" :key="`photo-${photo.id}`">
        <img :src="photo.thumbnailUrl" :alt="photo.title" />
      </li>
    </ul>
  </template>
  </Base>
</template>

<style lang="scss"></style>
