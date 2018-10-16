<template>
  <div id="app">
    <company></company>
    <h1 class="type">departure</h1>
    <search></search>
    <h1 class="type">arrival</h1>
    <search></search>

  </div>
</template>

<script>
import Vue from 'vue'
import Company from './components/company'
import Search from './components/search'
import VueResource from 'vue-resource'
import BootstrapVue from 'bootstrap-vue'
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'
import VueMq from 'vue-mq'

Vue.use(VueResource);
Vue.use(BootstrapVue);
Vue.use(VueMq, {
  breakpoints: {
    sm: 450,
    md: 1250,
    lg: Infinity,
  }
})

export default {
  name: 'App',
  components: {
    Company,
    Search
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
  background-color: antiquewhite;
}
.type {
  background-color: blanchedalmond;
  color: rgb(162, 162, 38);
}
</style>
