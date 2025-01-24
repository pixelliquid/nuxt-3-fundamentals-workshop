<script setup>
import { computed, ref } from 'vue'
// import Base from './Base.vue' - Nuxt infers this import from the component name

let photoGallery = ref([])

const route = useRoute()
console.log(route.query.album)

const filteredPhotoGallery = computed(() => {
  switch (route.query.album) {
    case 'even':
      return photoGallery.value.filter(item => item.albumId % 2 === 0)
    case 'odd':
      return photoGallery.value.filter(item => item.albumId % 2 !== 0)
    default:
      return photoGallery.value
  }
})
</script>

<template>
  <div class="container">
    <BaseDisplay title="Photo Gallery" v-model:itemList="photoGallery">
      <template v-slot:metrics>
        <pre>{{ filteredPhotoGallery.length }} photos</pre>
        <!-- <pre>{{ filteredPhotoGallery }}</pre> -->
      </template>
      <template v-slot:items>
        <li v-for="photo in filteredPhotoGallery" :key="`photo-${photo.id}`">
          <img :src="photo.thumbnailUrl" :alt="photo.id" />
        </li>
      </template>
    </BaseDisplay>
  </div>
</template>

<style lang="scss"></style>