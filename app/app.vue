<script setup></script>

<template>
  <TheNavbar />
  <NuxtPage />
</template>

<style lang="scss">
@import './node_modules/bulma/bulma.sass';
@import './assets/styles/main.scss';

.router-link-active,
a.navbar-item:hover,
a.navbar-item:focus {
  color: deeppink;
}
</style>
