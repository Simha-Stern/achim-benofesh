<script setup lang="ts">
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <div class="background">
    <img src="../public/logo.jpg" alt="logo" class="logo" />
  </div>
  <div class="content">
    <HelloWorld msg="" />
  </div>
</template>

<style scoped>
.background {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}

.logo {
  max-width: 90vw;
  max-height: 90vh;
  object-fit: contain;
  opacity: 0.2;
}

.content {
  position: relative;
  z-index: 1;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: default;
  /* will-change: filter; */
  /* transition: filter 300ms; */
}

.content:hover {
  /* filter: drop-shadow(0 0 2em #646cffaa); */
}
</style>
