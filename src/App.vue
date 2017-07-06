<template>
  <div id="app">
    <h1>Testing datetime input</h1>
    <hr>
    <datetime-input
            :label="label1"
            :options="options1">
    </datetime-input>

    <datetime-input
            :label="label2"
            :options="options2">
    </datetime-input>
  </div>
</template>

<script>
const flatpickr = require("flatpickr");
import datetimeInput from './datetime-imput.vue';

export default {
  name: 'app',
  data () {
    return {
      label1: 'Date and time',
      label2: 'Date range',
      options1: {
          enableTime: true,
      },
      options2: {
          mode: "range",
          enableTime: true,
      }
    }
  },
  components: {
      'datetime-input': datetimeInput
  },
}
</script>

<style>
/*@import '../node_modules/flatpickr/dist/themes/airbnb.css';*/

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
