<template>
  <div id="app">
    <Coinbase />
  </div>
</template>

<script>
import Coinbase from './components/Coinbase.vue';

export default {
  name: 'App',
  components: {
    Coinbase
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
