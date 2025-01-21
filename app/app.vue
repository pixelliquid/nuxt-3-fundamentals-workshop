<script setup>
import { computed, ref } from 'vue'
// import Base from './components/Base.vue' - Nuxt infers this import from the component name
// import TodoViewer from './components/TodoViewer.vue' - Nuxt infers this import from the component name
</script>

<template>
  <div class="section">
    <h1 class="title">Nuxt 3 Fundamentals course</h1>
  </div>
  <div class="section">
    <div class="columns">
      <div class="column">
        <TodoViewer title="This is fun!">
          <h2 class="subtitle">Does this really work?</h2>
          <template v-slot:hero>
            <h2 class="subtitle">This heading is slotted into the named "hero" slot</h2>
          </template>
          <!-- <template v-slot:metrics="slotProps"> -->
          <!-- <pre>{{ slotProps }}</pre> -->
          <template v-slot:metrics="{ completed, remaining }">
            <p>
              <strong>{{ completed.length }} items completed</strong> | {{ remaining.length }} remaining
            </p>
          </template>
        </TodoViewer>
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
