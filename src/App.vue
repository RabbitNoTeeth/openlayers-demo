<template>
  <div id="app">
    <openlayers-map></openlayers-map>
  </div>
</template>

<script>
import OpenlayersMap from "./components/OpenlayersMap";

export default {
  name: 'App',
  components: {
    OpenlayersMap
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
