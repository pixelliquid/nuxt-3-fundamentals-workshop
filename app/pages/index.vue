<script setup>
// useHead() is a composable for page metadata
useHead({
  title: 'Hello world'
})
</script>

<template>
  <div class="container">
    <div class="section">
      <NuxtLayout>
        <h1 class="title">Home</h1>
      </NuxtLayout>
    </div>
  </div>
</template>

<style lang="scss"></style>
