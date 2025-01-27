<script setup>
// useHead() is a composable for page metadata
useHead({
  title: 'Hello world'
})
</script>

<template>

  <!-- Nuxt config for page metadata -->
  <Html lang="">
  <Title>Merriweather Font</Title>
  <Link rel="preconnect" href="https://fonts.googleapis.com" />
  <Link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <Link rel="stylesheet"
    href="https://fonts.googleapis.com/css2?family=Inter:wght@100..900&family=Merriweather:ital,wght@0,300;0,400;0,700;0,900;1,300;1,400;1,700;1,900&display=swap" />

  </Html>

  <div class="container">
    <div class="section">
      <NuxtLayout>
        <h1 class="title">Home</h1>
      </NuxtLayout>
    </div>
  </div>
</template>

<style lang="scss">
body {
  font-family: 'Merriweather', serif;
}
</style>
