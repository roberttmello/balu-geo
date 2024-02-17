<script setup>
import { ref } from 'vue'

const countryName = ref('Brasil')

const countryCapitals = ref([
  { id: 0, name: 'Bogotá' },
  { id: 1, name: 'Brasília' },
  { id: 2, name: 'Cairo' },
  { id: 3, name: 'Berlim' },
  { id: 4, name: 'Camberra' }
])
</script>

<template>
  <main>
    <h1>Qual a capital do(a) {{ countryName }} ?</h1>
    <fieldset>
      <legend>Escolha uma opção:</legend>
      <div v-for="capital in countryCapitals" :key="capital.id">
        <input type="radio" :id="capital.id" name="capitalOption"/>
        <label :for="capital.id">{{capital.name}}</label>
      </div>
    </fieldset>
  </main>
</template>

<style scoped>
fieldset {
  border: none;
}
</style>
