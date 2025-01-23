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
          <NuxtLink to="/display/photos?album=even" class="navbar-item">Photos in even albums</NuxtLink>
          <NuxtLink to="/display/photos?album=odd" class="navbar-item">Photos in odd albums</NuxtLink>
          <NuxtLink to="/display/todos" class="navbar-item">Todos</NuxtLink>
          <NuxtLink to="/display/todos?completed=false" class="navbar-item">Open todos</NuxtLink>
          <NuxtLink to="/display/todos?completed=true" class="navbar-item">Completed todos</NuxtLink>
        </div>
      </div>
    </div>
  </nav>
</template>

<style></style>