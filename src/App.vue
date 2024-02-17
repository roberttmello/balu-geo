<script setup>
import NavBar from './components/NavBar.vue'
import MainContent from './components/MainContent.vue'
import FooterContent from './components/FooterContent.vue'
</script>

<template>
  <div class="appContainer">
    <NavBar />
    <MainContent />
    <FooterContent />
  </div>
</template>

<style scoped>
 .appContainer {
  max-width: 1200px;
  min-height: 100vh;
  display: flex;
  justify-content: space-between;
  margin: 40px auto;
  flex-direction: column;
 }

</style>
