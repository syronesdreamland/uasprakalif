<template>
  <div class="weathery">Weather Today</div>
  
  <div class="date">
    <div class="time">
      <h5>{{ formattedDate }}</h5>
    </div>
  </div>
  <div class="search-bar">
    <input v-model="city" placeholder="Enter city name" @keyup.enter="getWeather" />
    <button @click="getWeather">Search</button>
  </div>
  <div class="weather-widget">
    <h2>Weather Info</h2>
    <div v-if="weather" class="weather-info">
          <p class="bold-text-name"> {{ weather.name }}</p>
          <p class="bold-text-temp"> {{ weather.main.temp }}°C</p>
          <p class="bold-text-desc"> {{ weather.weather[0].description }} </p>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import axios from 'axios'

const city = ref('')
const weather = ref(null)
const time = ref('')
const formattedDate = ref(formatDate(new Date()))

const getWeather = async () => {
  const apiKeyWeather = 'ceb97d9ca273e7696ff7f99b1a1fa728'
  const apiKeyTime = 'M39X87MJFWNP'
  const urlWeather = `https://api.openweathermap.org/data/2.5/weather?q=${city.value}&units=metric&appid=${apiKeyWeather}`

  try {
    const responseWeather = await axios.get(urlWeather)
    weather.value = responseWeather.data
    
    const urlTime = `http://api.timezonedb.com/v2.1/get-time-zone?key=${apiKeyTime}&format=json&by=position&lat=${weather.value.coord.lat}&lng=${weather.value.coord.lon}`
    const responseTime = await axios.get(urlTime)
    time.value = responseTime.data.formatted
    formattedDate.value = formatDate(new Date(responseTime.data.formatted))
  } catch (error) {
    console.error(error)
    weather.value = null
    time.value = ''
  }
}

// Helper function to format the date
function formatDate(date) {
  const options = { weekday: 'long', day: 'numeric', month: 'long', year: 'numeric' }
  return new Intl.DateTimeFormat('en-US', options).format(date)
}
</script>

<style scoped>
.weathery {
  margin: 30px 180px;
  text-align: left;
  font-size: 36px;
  font-weight: 700;
}

.time h5 {
  margin: 20px 180px;
  text-align: left;
  opacity: 0.5;
}
.search-bar {
  display: flex;
  justify-content: flex-end;
  margin: 20px 180px;
  position: absolute;
  top: 0;
  right: 0;
}

.search-bar input {
  padding: 10px;
  width: 90%;
  margin: 2px 10px;
  color:#4b4b4b;
  border: 1px solid #d3d3d3;
  border-radius: 20px;
  background-color: rgb(247, 247, 247);
}

.search-bar input:hover {
  transform: scale(1.01);
}

.search-bar button {
  padding: 10px;
  border: 1px solid white;
  background-color:#FF6969;
  color: white;
  cursor: pointer;
  border-radius: 10px;
}

.search-bar button:hover {
  background-color: white;
  color: #FF6969;
  border: 1px solid #FF6969;
  transition: 0.5s;
}

.weather-widget {
  border: 1px solid var(--medium-red);
  border-radius: 10px;
  max-width: 1000px;
  margin: 50px 180px; 
  text-align: left;
  background-color: #FF6969;
  color:white;
}

.weather-widget:hover{
  transform:scale(1.01)
}

.weather-widget h2 {
  font-size: 36px;
  font-weight: bold;
  margin-bottom: 20px;
  padding: 20px;
}

.weather-info {
  display: block;
  justify-content: center; 
  align-items: center;
  margin-left: 20px;
  padding: 10px;
  font-weight: 500;
  font-size: 20px;
}

  


.weather-bawah {
  margin: 200px 200px;
}

.weather-item {
  margin: 20px 200px; /* Adjusted for more space */
  border: 1px solid white;
  border-radius: 5px;
  padding: 20px;
  background-color: #FF6969;
  text-align: center;
  width: 220px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  animation: backgroundColorChange 3s ease infinite; /* Added background animation */
}

  .weather-border {
  border-top: 1px solid var(--medium-red);
  margin-top: 10px;
  padding-top: 10px;
}

</style>
