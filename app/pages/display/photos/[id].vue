<script setup>
const route = useRoute()
</script>

<template>
  <div class="section">
    <h2 class="title">This is photo id: {{ route.params }}</h2>
    <NuxtLink to="/display/photos">Back to Photos</NuxtLink>
  </div>
</template>

<style lang="scss"></style>
