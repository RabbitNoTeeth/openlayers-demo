<template>
  <div id="map"></div>
</template>

<script>
import {Map, View} from 'ol';
import TileLayer from 'ol/layer/Tile';
import XYZ from 'ol/source/XYZ';
import Projection from 'ol/proj/Projection';

export default {
  name: "OpenlayersMap",
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
      const bounds = [1.3079709473624736E7,4707873.362584061,1.328190134012295E7,4933520.149300369];
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
              url: "http://192.168.3.65:8080/geoserver/gwc/service/tms/1.0.0/tangshan_tiles%3Ats_tile_level_13@EPSG%3A3857@png/{z}/{x}/{-y}.png"
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