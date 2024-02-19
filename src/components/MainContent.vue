<script setup>
import { ref, onMounted, nextTick } from 'vue'
import ConfettiExplosion from 'vue-confetti-explosion'

const apiURL = 'https://restcountries.com/v3.1/all?fields=name,capital'
let randomIndexCountry = Math.floor(Math.random() * 193)

const countriesData = ref(null)
const currentCountryName = ref('')
const currentCountryCapitalsOptions = ref([])
const score = ref(0)
const answer = ref('')
const celebrateTime = ref(false)

async function celebrate() {
  celebrateTime.value = false
  await nextTick()
  celebrateTime.value = true
}

function calcScore(capitalSelected) {
  if (capitalSelected === answer.value) {
    score.value++
    celebrate()
  }
  generateQuiz()
}

function generateQuiz() {
  currentCountryCapitalsOptions.value = []
  for (let index = 0; index < 5; index++) {
    randomIndexCountry = Math.floor(Math.random() * 250)
    currentCountryCapitalsOptions.value.push({
      id: index,
      name: countriesData.value[randomIndexCountry].capital[0],
      countryIndex: randomIndexCountry
    })
  }
  let randomPosQuestion = Math.floor(Math.random() * 5)
  let indexCountryQuestion = currentCountryCapitalsOptions.value[randomPosQuestion].countryIndex
  currentCountryName.value = countriesData.value[indexCountryQuestion].name.common
  answer.value = countriesData.value[indexCountryQuestion].capital[0]
}

onMounted(() => {
  async function fetchDataCountries() {
    const response = await fetch(apiURL)
    countriesData.value = await response.json()
    localStorage.setItem('countriesDataLocal', countriesData.value)
    generateQuiz()
  }

  if (countriesData.value === null) {
    fetchDataCountries()
  }
})
</script>

<template>
  <h2>
    What's the capital of <span class="countryName">{{ currentCountryName }}</span> ?
  </h2>
  <span class="score">Score: {{ score }}</span>
  <main>
    <ConfettiExplosion v-if="celebrateTime" :particleCount="200" :force="0.3" :duration="1000" />
    <ul class="listCountry">
      <li
        v-for="capital in currentCountryCapitalsOptions"
        :key="capital.id"
        class="listCountryItem"
        @click="calcScore(capital.name)"
      >
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

.score {
  font-size: 1.5rem;
  font-weight: bold;
  display: flex;
  justify-content: right;
  align-items: center;
}

.countryName {
  color: var(--primary-color);
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
