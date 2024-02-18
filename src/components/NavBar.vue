<script setup>
import { ref } from 'vue'

const buttonThemeLabel = ref('Dark')
</script>

<template>
  <nav>
    <div>
      <a href="/"> <img src="/logo.svg" alt="Logo Image" class="logo" /></a>
    </div>
    <div>
      <button>{{ buttonThemeLabel }}</button>
    </div>
  </nav>
</template>

<style scoped>
nav {
  height: 128px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.logo {
  max-width: 256px;
}

button {
  background-color: transparent;
  border: 2px solid var(--primary-color);
  padding: 8px 32px;
  font-weight: bold;
  cursor: pointer;
}

button:hover {
  background-color: var(--primary-color);
  transition: 0.3s;
}
</style>
