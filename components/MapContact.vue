<template>
  <GMap ref="gmap" :center="center" :zoom="12" style="height: 100%;" :options="options">
    <GMapMarker :position="{lat: 40.711631,lng: -74.006641}" :options="markerOptions"></GMapMarker>
  </GMap>
</template>

<script>
const mapMarker = require("@/assets/image/marker.png");
export default {
  name: "map-contact",
  data() {
    return {
      markerOptions: {
        icon: {
          url: mapMarker,
          size: { width: 60, height: 60, f: "px", b: "px" },
          scaledSize: { width: 40, height: 40, f: "px", b: "px" },
        },
      },
      options: {
        zoomControl: false,
        mapTypeControl: false,
        scaleControl: false,
        streetViewControl: false,
        rotateControl: false,
        fullscreenControl: false,
      },
      center: { lat: 40.711631, lng: -74.006641 },
    };
  },
};
</script>