<script>
import { format } from 'date-fns';

const API_URL = `https://api.openweathermap.org/data/2.5/weather?lat=43.1940&lon=-80.3845&appid=8ad493940057ce1f08e48316a3194a8c&units=metric`

export default {
  data () {
    return {
      format,
      weather: null
    }
  },

  created() {
    this.fetchData()
  },

  methods: {
    async fetchData() {
      const weatherData = await (await fetch(API_URL)).json()
      this.weather = Math.round(weatherData.main.temp)
    },
    getCurrentDateTime() {
      return format(new Date(), 'yyyy-MM-dd HH:mm:ss');
    }
  }
}

</script>

<template>

  <WelcomeItem>
    
    <h2>Date/Time</h2>
    <p>The current date and time is: {{getCurrentDateTime()}}</p>
    <br>
    <h2>Temperature</h2>
    <p> The current temperature in Paris, Ontario is: {{ weather }}°C</p>
  </WelcomeItem>

  
</template>
