<script setup></script>

<template>
  <nav class="navbar" role="navigation" aria-label="main navigation">
    <div class="navbar-brand">
      <NuxtLink to="/" class="navbar-item">Home</NuxtLink>
    </div>

    <div id="navbarBasicExample" class="navbar-menu">
      <div class="navbar-end">
        <NuxtLink to="/display" class="navbar-item">Display</NuxtLink>
        <NuxtLink to="/display/photos" class="navbar-item">Photos</NuxtLink>
        <NuxtLink to="/display/todos" class="navbar-item">Todos</NuxtLink>
      </div>
    </div>
  </nav>
</template>

<style></style>
