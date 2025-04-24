<template>
  <div class="weather-widget">
    <h2>Weather in {{ city }}</h2>
    <p v-if="weather">{{ weather.main.temp }}°C - {{ weather.weather[0].description }}</p>
    <p v-else>Loading...</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      city: "Berlin",
      weather: null
    };
  },
  mounted() {
    fetch(`https://api.openweathermap.org/data/2.5/weather?q=${this.city}&units=metric&appid=YOUR_API_KEY`)
      .then(res => res.json())
      .then(data => this.weather = data);
  }
}
</script>

<style scoped>
.weather-widget {
  font-family: Arial, sans-serif;
  color: #333;
  padding: 20px;
}
</style>
