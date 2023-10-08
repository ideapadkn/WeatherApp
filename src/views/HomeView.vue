<script setup>
import { ref } from 'vue';

const apiKey = ref('2ad213d1b639694377f42b93faafc162')
const urlBase = ref('https://api.openweathermap.org/data/3.0/')
const query = ref('')
const weather = ref({})

const fetchWeather = (e) => {
  if (e.key == 'Enter') {
    fetch(`${urlBase.value}onecall?lat={lat}&lon={lon}&exclude={part}&appid=${apiKey.value}`)
      .then(res => {
        return res.json()
      }).then(setResults)
  }
}

const setResults = (results) => {
  weather.value = results
}

</script>

<template>
  <main class="main">
    <div class="container mx-auto pt-5">
      <div class="search-box mb-5">
        <input class="search-bar block w-full p-4 border-none outline-none" v-model="query" @keypress="fetchWeather"
          type="text" placeholder="search...">
      </div>
      <div class="weather-wrap" v-if="(typeof weather.main != 'undefined')">
        <div class="location-box text-center mb-5">
          <div class="location text-white text-3xl font-medium mb-1">{{ weather.name }}, {{ weather.sys.country }}</div>
          <div class="date text-white text-lg font-light italic">Monday 20 January 2023</div>
        </div>
        <div class="weather-box text-center">
          <div class="temp py-3 px-6 text-white text-8xl font-black rounded-2xl inline-block mb-5">9^</div>
          <div class="weather text-white text-5xl font-bold italic">Rain</div>
        </div>
      </div>
    </div>
  </main>
</template>

<style lang="scss">
.main {
  background-image: linear-gradient(to bottom, rgba(0, 0, 0, 0.25), rgba(0, 0, 0, 0.75));
  height: 100vh;
}

.search-bar {
  color: #313131;
  font-size: 20px;
  border-radius: 0 16px 0 16px;
  background-color: rgba(255, 255, 255, .5);
  box-shadow: 0px 0px 8px rgba(0, 0, 0, .25);
  transition: .4s;

  &:focus {
    box-shadow: 0px 0px 16px rgba(0, 0, 0, .25);
    background-color: rgba(255, 255, 255, .9);
    border-radius: 16px 0 16px 0;

  }
}

.location {
  text-shadow: 1px 3px rgba(0, 0, 0, .25);
}

.temp {
  text-shadow: 3px 6px rgba(0, 0, 0, .25);
  background-color: rgba(255, 255, 255, .25);
  box-shadow: 3px 6px rgba(0, 0, 0, .25);
}

.weather {
  text-shadow: 3px 6px rgba(0, 0, 0, .25);

}
</style>