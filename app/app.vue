<script setup>
import { computed, ref } from 'vue'
import PhotoGallery from './components/PhotoGallery.vue'
import TodoViewer from './components/TodoViewer.vue'
</script>

<template>
  <div class="section">
    <h1 class="title">Hello world</h1>
  </div>
  <div class="section">
    <div class="columns">
      <div class="column">
        <TodoViewer />
      </div>
      <div class="column">
        <PhotoGallery />
      </div>
    </div>
  </div>
</template>

<style lang="scss">
@import './node_modules/bulma/bulma.sass';
@import './assets/styles/main.scss';
</style>
