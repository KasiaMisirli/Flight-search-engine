<template>
  <div id="app">
    <company></company>
    <h1 class="type">departure</h1>
    <search class="firstFlight"></search>
    <h1 class="type">arrival</h1>
    <search class="secondFlight"></search>
  </div>
</template>

<script>
import Vue from 'vue'
import Company from './components/company'
import Search from './components/search'
import BootstrapVue from 'bootstrap-vue'
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'
import axios from 'axios'
import VueAxios from 'vue-axios'
import SpinnerButton from './components/spinnerbutton'

Vue.component('SpinnerButton', { /* ... */ })
Vue.use(VueAxios, axios);
Vue.use(SpinnerButton);
Vue.use(BootstrapVue);

export default {
  name: 'App',
  components: {
    Company,
    Search,
    SpinnerButton
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.type {
  background-color: blanchedalmond;
}
body {
  background-color: mistyrose;
}
</style>
