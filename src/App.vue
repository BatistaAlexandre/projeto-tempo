<template>
  <div>
    <h1>Weather Forecast App</h1>
    <input v-model="city" placeholder="Enter city name" />
    <button @click="fetchWeather">Get Weather</button>

    <div v-if="weather">
      <h2>{{ weather.name }}</h2>
      <p>{{ weather.main.temp }}°C</p>
      <p>{{ weather.weather[0].description }}</p>

      <!-- Exibição do ícone de acordo com o tipo de tempo -->
      <component :is="getWeatherIcon(weather.weather[0].icon)" size="48" />
    </div>
  </div>
</template>

<script>
import { ref } from 'vue';
import axios from 'axios';
import { Sun, Cloud, CloudDrizzle, CloudRain, CloudLightning, CloudSnow, CloudFog } from 'vue-feather-icons';
import { sun } from 'vue-feather-icons';
export default {
  name: 'App',
  components: {
    Sun,
    Cloud,
    CloudDrizzle,
    CloudRain,
    CloudLightning,
    CloudSnow,
    CloudFog,
  },
  setup() {
    const city = ref('');
    const weather = ref(null);

    const fetchWeather = async () => {
      try {
        const response = await axios.get(
          `https://api.openweathermap.org/data/2.5/weather?q=${city.value}&units=metric&appid=5946f7a35af123ae4d75fc2eb4593288`
        );
        weather.value = response.data;
      } catch (error) {
        console.error(error);
      }
    };

    const getWeatherIcon = (iconCode) => {
      switch (iconCode) {
        case '01d':
          return 'Sun';
        case '01n':
          return 'Moon';
        case '02d':
        case '02n':
        case '03d':
        case '03n':
        case '04d':
        case '04n':
          return 'Cloud';
        case '09d':
        case '09n':
          return 'CloudDrizzle';
        case '10d':
        case '10n':
          return 'CloudRain';
        case '11d':
        case '11n':
          return 'CloudLightning';
        case '13d':
        case '13n':
          return 'CloudSnow';
        case '50d':
        case '50n':
          return 'CloudFog';
        default:
          return 'Sun';
      }
    };

    return {
      city,
      weather,
      fetchWeather,
      getWeatherIcon,
    };
  },
};
</script>
