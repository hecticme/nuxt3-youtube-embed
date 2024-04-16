<script setup lang="ts">
useHead({
  title: 'Youtube Embedded Iframe',
})
</script>

<template>
  <main class="app-wrapper">
    <YoutubeEmbed />
  </main>
</template>

<style scoped>
.app-wrapper {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
