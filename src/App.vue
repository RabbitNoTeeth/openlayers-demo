<template>
  <div id="app">
    <el-tabs v-model="activeName">
      <el-tab-pane label="XYZ加载TMS瓦片地图" name="1">
        <LoadTMSByXYZ v-if="activeName === '1'"></LoadTMSByXYZ>
      </el-tab-pane>
      <el-tab-pane label="XYZ加载WMTS瓦片地图" name="2">
        <LoadWMTSByXYZ v-if="activeName === '2'"></LoadWMTSByXYZ>
      </el-tab-pane>
      <el-tab-pane label="加载WMTS瓦片地图" name="3">
        <LoadWMTS v-if="activeName === '3'"></LoadWMTS>
      </el-tab-pane>
    </el-tabs>
  </div>
</template>

<script>
import LoadTMSByXYZ from "./components/LoadTMSByXYZ";
import LoadWMTSByXYZ from "./components/LoadWMTSByXYZ";
import LoadWMTS from "./components/LoadWMTS";

export default {
  name: 'App',
  components: {
    LoadWMTS,
    LoadWMTSByXYZ,
    LoadTMSByXYZ
  },
  data() {
    return {
      activeName: '2'
    }
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
