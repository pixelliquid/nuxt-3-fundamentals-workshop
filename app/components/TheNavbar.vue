<script setup></script>

<template>
  <nav class="navbar" role="navigation" aria-label="main navigation">
    <div class="navbar-brand">
      <NuxtLink to="/" class="navbar-item">MyRecs</NuxtLink>
      <NuxtLink to="/display" class="navbar-item">Display</NuxtLink>
      <div class="navbar-item has-dropdown is-hoverable">
        <div class="navbar-link">Display options</div>
        <div class="navbar-dropdown">
          <NuxtLink to="/display/photos" class="navbar-item">Photos</NuxtLink>
          <NuxtLink to="/display/todos" class="navbar-item">Todos</NuxtLink>
        </div>
      </div>
    </div>
  </nav>
</template>

<style></style>
