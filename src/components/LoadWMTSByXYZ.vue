<template>
  <div id="map"></div>
</template>

<script>
import {Map, View} from 'ol';
import TileLayer from 'ol/layer/Tile';
import XYZ from 'ol/source/XYZ';
import Projection from 'ol/proj/Projection';

export default {
  name: "LoadWMTSByXYZ",
  data() {
    return {
      map: null
    }
  },
  mounted() {
    this.initMap();
  },
  methods: {
    initMap() {
      const app = this;
      const bounds = [13203197.206783397, 4788454.964696088, 13218733.03278226, 4799595.661568641];
      const map = new Map({
        target: 'map',
        view: new View({
          projection: new Projection({
            code: 'EPSG:3857',
            units: 'm',
            global: false
          })
        }),
        layers: [
          new TileLayer({
            source: new XYZ({
              url: "http://localhost:8080/geoserver/gwc/service/tms/1.0.0/LuanNan%3ALuanNan_tiles@EPSG%3A3857x18@png/{z}/{x}/{-y}.png"
            })
          })
        ]
      });
      map.getView().fit(bounds, map.getSize());
      app.map = map;
    }
  }
}
</script>

<style scoped>

#map {
  width: 1000px;
  height: 800px;
  border: 1px solid black;
}

</style>