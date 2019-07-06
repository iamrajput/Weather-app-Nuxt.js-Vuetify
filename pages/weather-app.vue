<template>
<v-container>
<h1 class="display-1 text-xs-center">Weather app</h1>
<v-flex xs12>
<v-card color="#F9A825" dark>
<v-card-text>
<v-layout justify-center v-if="weather.weather">
<v-flex class="text-xs-center" xs4>
<h4>Temperature</h4>
<h1 class="display-1">{{weather.name}}</h1>
<img :src="icon" alt="weather icon">
<p><span class="display-1">{{ temp() }} &deg;c</span></p>
<span class="caption ml-4"><b>{{this.weather.weather[0].description}}</b></span>
</v-flex>
<v-flex class="text-xs-center" xs4>
<h4>Wind and Pressure</h4>
<h3 class="headline">Wind: {{weather.wind.speed}} m/s</h3>
<h3 class="headline mt-4">Humidity: {{weather.main.humidity}}%</h3>
<h3 class="headline mt-4">Pressure: {{weather.main.pressure}} hPa</h3>
</v-flex>
<v-flex class="text-xs-center" xs4>
<h4>Others Information</h4>
<h3 class="headline">Max Temperature: {{ Math.round(weather.main.temp_max - 273)}} &deg;c</h3>
<h3 class="headline mt-4">Min Temperature: {{ Math.round(weather.main.temp_min - 273)}} &deg;c</h3>
<h3 class="headline mt-4">Visibility: {{ weather.visibility}} candelas</h3>
</v-flex>
</v-layout>
</v-card-text>
</v-card>
</v-flex>
<v-flex xs12 mt-4>
<v-form @submit.prevent="getWeather">
      <v-text-field
        label="Enter city name" solo
       v-model="city" >
</v-text-field>
</v-form>
 </v-flex>

</v-container>
 
 
</template>

<script>
export default {
  data() {
    return {
      city:"London",
      weather:{}
    }
  },
  computed:{
    icon(){
      return this.weather.weather ? `https://openweathermap.org/img/wn/${this.weather.weather[0].icon}.png` : ''
    }
  },
  created() {
     this.getWeather();
     this.temp();
  },

  methods: {
    getWeather(){
       this.$axios
        .$get(`https://api.openweathermap.org/data/2.5/weather?q=${this.city}&appid=28d0ab8fb118d853781624328189de56`).then(res => (this.weather = res))

    },
    temp(){
      return this.weather.weather ? Math.round(this.weather.main.temp -273) : '';
    }
  },
  
  }
</script>
