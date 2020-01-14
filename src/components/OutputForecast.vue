<template>
  <div>
    <ul class="forecast">
      <li class="forecast__item item" v-for="forecast in allDataForecast.list" :key="forecast.id">
        <div class="item__time">{{ forecast.dt_txt }}</div>
        <img class="weather-ico" :src="'http://openweathermap.org/img/w/' + forecast.weather[0].icon + '.png'"  :alt="forecast.weather[0].main">
        <div>{{ Math.round(forecast.main.temp) }}&deg;</div>
        <div>{{ forecast.weather[0].description }}</div>
      </li>
    </ul>
  </div>
</template>

<script>

export default {
  name: 'OutputForecast',
  props: ['allDataForecast', 'regionForecast']
}
</script>

<style scoped>
  h2 {
    text-align: center;
  }
  .forecast {
    display: flex;
    flex-wrap: wrap
  }
  .forecast__item {
    display: flex;
    flex-direction: column;
    width: 300px;
    margin: 20px;
    padding: 20px 0;
    background-color: #999;
    box-shadow: 0 0 10px #000;
    text-align: center;
  }
  .forecast__item .weather-ico {
    display: block;
    margin: 0 auto;
    width: 50px;
    height: 50px;
  }
</style>
