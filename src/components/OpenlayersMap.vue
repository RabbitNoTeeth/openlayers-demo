<template>
  <div id="map"></div>
</template>

<script>
import {Map, View} from 'ol';
import TileLayer from 'ol/layer/Tile';
import TileWMS from 'ol/source/TileWMS';
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
      const bounds = [983797.5, 207443, 991899.0625, 218850.828125];
      const map = new Map({
        target: 'map',
        view: new View({
          projection: new Projection({
            code: 'EPSG:2908',
            units: 'm',
            global: false
          })
        }),
        layers: [
          new TileLayer({
            source: new TileWMS({
              projection: 'EPSG:2908',
              url: 'http://localhost:8080/geoserver/nyc_roads/wms',
              params: {
                'LAYERS': 'nyc_roads:nyc_buildings',
                'FORMAT': 'image/png',
                'VERSION': '1.1.1',
              }
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
  width: 100%;
  height: 800px;
}

</style>