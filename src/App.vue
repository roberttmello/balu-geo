<script setup>
import NavBar from './components/NavBar.vue'
import MainContent from './components/MainContent.vue'
import FooterContent from './components/FooterContent.vue'

// import allCountries from './data/countries.js'
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
  height: 100vh;
  display: flex;
  justify-content: space-between;
  margin: 0px auto;
  padding: 0px 32px;
  flex-direction: column;
}
</style>
