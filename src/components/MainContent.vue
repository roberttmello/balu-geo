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
  <main>
    <h2>Qual a capital do(a) {{ currentCountryName }} ?</h2>
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
  margin-bottom: 16px;
}

main {
  display: grid;
  place-content: center;
}

.listCountryItem {
  width: 340px;
  height: 48px;
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
