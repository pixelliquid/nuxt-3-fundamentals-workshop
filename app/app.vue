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
a.navbar-item:focus,
.navbar-link:hover,
.navbar-link:focus,
.navbar-dropdown a.navbar-item:hover {
  color: deeppink;
}

.navbar-link:not(.is-arrowless)::after {
  border-color: currentColor;
}
</style>
