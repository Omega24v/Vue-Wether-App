<template>
  <div id="app">
    <h1>Weather Forecast Widget</h1>
    <SearchForecast
      :regionForecast="regionForecast"
      :requestForecast="requestForecast"
    />
    <OutputForecast
      :allDataForecast="allDataForecast"
      :requestForecast="requestForecast"
      :regionForecast="regionForecast"
    />
  </div>
</template>

<script>
// IMPORTS COMPONENTS
import OutputForecast from './components/OutputForecast'
import SearchForecast from './components/SearchForecast'

export default {
  components: {
    'OutputForecast': OutputForecast,
    'SearchForecast': SearchForecast
  },
  data() {
    return {
      openWeatherApi: {
        key: 'e038d75a0bc30648ea05cc11d6253b56',
        cnt: '10'
      },
      regionForecast: {
        city: 'Cherkasy',
        country: {
          selected: 'ua',
          options: ['ua', 'ger']
        }
      },
      allDataForecast: {
        type: Array,
        default: []
      }
    }
  },
  methods: {
    requestForecast: function() {
      const baseURI = 'https://api.openweathermap.org/data/2.5/forecast?q=' + this.regionForecast.city + ',' + this.regionForecast.country + '&cnt=' + this.openWeatherApi.cnt + '&units=metric&lang=ru&appid=' + this.openWeatherApi.key + ''
      this.$axios.get(baseURI)
        .then((result) => {
          this.allDataForecast = result.data
        })
    }
  }
}
</script>

<style>
  h1 {
    text-align: center;
  }
  body {
    font-family: 'Arial', Courier, monospace;
  }
</style>
