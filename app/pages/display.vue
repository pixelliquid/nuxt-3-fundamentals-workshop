<script setup></script>

<template>
  <div class="container">
    <div class="section">
      <h1 class="title">Display</h1>
      <h2>Choose a display option:</h2>
      <div class="buttons">
        <NuxtLink to="/display/photos" class="button">Photos</NuxtLink>
        <NuxtLink to="/display/todos" class="button">Todos</NuxtLink>
      </div>
      <NuxtPage /><!-- like <slot> -->
    </div>
  </div>
</template>

<style></style>
 