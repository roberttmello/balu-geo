<script setup>
import { ref } from 'vue'

const currentCountryName = ref('Brasil')

const currentCountryCapitalsOptions = ref([
  { id: 0, name: 'Bogotá' },
  { id: 1, name: 'Brasília' },
  { id: 2, name: 'Cairo' },
  { id: 3, name: 'Berlim' },
  { id: 4, name: 'Camberra' }
])
</script>

<template>
  <h2>Qual a capital do(a) {{ currentCountryName }} ?</h2>
  <main>
    <ul class="listCountry">
      <li v-for="capital in currentCountryCapitalsOptions" :key="capital.id" class="listCountryItem">
        {{ capital.name }}
      </li>
    </ul>
  </main>
</template>

<style scoped>
h2 {
  text-align: center;
}

main {
  display: grid;
  place-content: center;
  margin-top: -32px;
}

.listCountryItem {
  width: 256px;
  height: 32px;
  border: 2px solid var(--primary-color);
  margin-bottom: 16px;
  padding: 4px;
  display: grid;
  place-content: center;
  font-weight: bold;
}

.listCountryItem:hover {
  background-color: var(--primary-color);
  transition: 0.3s;
  cursor: pointer;
}
</style>
