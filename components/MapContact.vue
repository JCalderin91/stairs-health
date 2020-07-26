<template>
  <gmap-map ref="gmap" :center="center" :zoom="12" style="height: 100%;" :options="options">
    <gmap-marker :position="{lat: 40.711631,lng: -74.006641}" :icon="markerOptions" >
    </gmap-marker>
  </gmap-map>
</template>

<script>
import Card from '@/components/Card'
const mapMarker = require('@/assets/image/marker.png');
export default {
  components: {
    Card
  },
  name: "GoogleMap",
  data() {
    return {
      markerOptions: {
        url: mapMarker,
        size: {width: 60, height: 60, f: 'px', b: 'px',},
        scaledSize: {width: 40, height: 40, f: 'px', b: 'px',},
      },
      //a default center for the map
      options: {
        zoomControl: false,
        mapTypeControl: false,
        scaleControl: false,
        streetViewControl: false,
        rotateControl: false,
        fullscreenControl: false
      },
      center: {lat: 40.711631,lng: -74.006641},
      map: null,
       infoWindowPos: {
        lat: 0,
        lng: 0
      },
      currentMidx: null,
      //optional: offset infowindow so it visually sits nicely on top of our marker

    };
  }
};
</script>