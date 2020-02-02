<template>
  <q-page class="col">
    <div id="mapa">
      <gmap-map
        :center="center"
        :zoom="zoom"
        :options="options"
        style="width: 100%; height: 450px;">
        <gmap-marker v-for="(marker) in markers"
          :key="marker.key"
          :position="marker"
          :icon="icon"
        >
        </gmap-marker>
        <gmap-polygon :paths="paths" :editable="false" :draggable="false"></gmap-polygon>
      </gmap-map>
  </div>
  </q-page>
</template>

<script>
import Vue from 'vue'
import * as VueGoogleMaps from 'vue2-google-maps'

import { paths } from '../statics/paths'

Vue.use(VueGoogleMaps, {
  load: {
    key: 'tu-api-key'
  }
})

export default {
  name: 'PageIndex',
  data () {
    return {
      center: {
        lat: 36.60338869729776,
        lng: -4.643738644531254
      },
      zoom: 7,
      markers: [
        { lat: 36.71395099999999, lng: -4.432000000000016 },
        { lat: 36.51007199999999, lng: -4.882447400000046 }
      ],
      options: {
        zoomControl: true, // Establece el control de zoom del mapa
        mapTypeControl: false, // Oculta el control de tipos de mapas
        scaleControl: false, //  Oculta el control de escala del mapa
        streetViewControl: false, // Oculta el control de StreeView del mapa
        fullscreenControl: true // Establce el control full screen para ver el mapa a pantalla completa
      },
      icon: '/statics/marker.png',
      paths: paths
    }
  }
}
</script>
