<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <Blocks/>
  </div>
</template>

<script>
import Blocks from './components/Blocks.vue'

export default {
  name: 'App',
  components: {
    Blocks
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
  margin-top: 0px;
}
</style>
