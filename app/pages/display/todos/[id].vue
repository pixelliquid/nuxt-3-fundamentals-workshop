<script setup>
const route = useRoute()
</script>

<template>
  <div class="section">
    <h2 class="title">This is task id: {{ route.params.id }}</h2>
    <NuxtLink to="/display/todos">Back to Todos</NuxtLink>
  </div>
</template>

<style lang="css"></style>
