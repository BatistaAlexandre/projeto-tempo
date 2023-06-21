<script setup lang="ts">
import { ref } from 'vue'

defineProps<{ msg: string }>()

const count = ref(0)
</script>

<template>
  <h1>{{ msg }}</h1>

  <div class="card">
    <button type="button" @click="count++">count is {{ count }}</button>
    <p>
      Edit
      <code>components/HelloWorld.vue</code> to test HMR
    </p>
  </div>

  <p>
    Check out
    <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank"
      >create-vue</a
    >, the official Vue + Vite starter
  </p>
  <p>
    Install
    <a href="https://github.com/vuejs/language-tools" target="_blank">Volar</a>
    in your IDE for a better DX
  </p>
  <p class="read-the-docs">Click on the Vite and Vue logos to learn more</p>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>



<!-- 

<template>
  <div>
    <h1>Weather Forecast App</h1>
    <input v-model="city" placeholder="Enter city name" />
    <button @click="fetchWeather">Get Weather</button>
    <img :src="countryFlag" style="height: 20px;"/>

    <div v-if="weather">
      <h2>{{ weather.name }}</h2>
      <p>{{ weather.main.temp }}°C</p>
      <p>{{ weather.weather[0].description }}</p>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue';
import axios from 'axios';

export default {
  name: 'App',
  setup() {
    const city = ref('');
    const weather = ref(null);
    // const countryFlag = `https://flagsapi.com/:${}/:style/:size.png`
    var countryFlag = `https://flagsapi.com/BR/flat/64.png`
    const fetchWeather = async () => {
      try {
        const response = await axios.get(
          `https://api.openweathermap.org/data/2.5/weather?q=${city.value}&units=metric&appid=5946f7a35af123ae4d75fc2eb4593288`
        );
        weather.value = response.data;
        countryFlag =  `https://flagsapi.com/${weather.value.sys.country}/flat/64.png`
        console.log(countryFlag)
      } catch (error) {
        console.error(error);
      }
    };

    return {
      city,
      weather,
      fetchWeather,
      countryFlag
    };
  },
};
</script> -->