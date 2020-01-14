<template>
  <div>
    <form v-on:submit.prevent>
      <div>
        <label for="city">City</label>
        <input type="text" id="city" name="field-city" v-model="regionForecast.city" placeholder="enter city" required>
      </div>
      <div>
        <label for="country">Country</label>
        <select name="country-select" v-model="regionForecast.country.selected"> <!--Supplement an id here instead of using 'name'-->
          <option v-for="countries in regionForecast.country.options" :key="countries">{{countries}}</option>
        </select>
      </div>
      <button type="submit" @click="requestForecast">Show weather</button>
    </form>
  </div>
</template>

<script>

export default {
  name: 'SearchForecast',
  props: ['regionForecast', 'requestForecast']
}
</script>

<style scoped>
  h2 {
    text-align: center;
  }
  form {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 600px;
    margin: 0 auto;
    padding: 20px;
    background-color: #999;
    box-shadow: 0 0 10px #000
  }
  form label {
    padding: 0 10px;
  }
  form input {
    padding: 10px;
    border: none;
    border-radius: 20px;
    background-color: #fff;
  }
  form select {
    border: none;
    padding: 9px;
    text-transform: uppercase;
  }
  form button {
    margin-left: 20px;
    border: none;
    padding: 10px;
    background-color: #fff;
  }
</style>
