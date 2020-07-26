<template>
    <gmap-map
      ref="gmap"
      :center="center"
      :zoom="12"
      style="height: 100%;"
      :options="options"
    >
      
      <gmap-marker
        :key="index"
        v-for="(m, index) in markers"
        :position="m.position"
        :icon="markerOptions"
        @click="toggleInfoWindow(m,index)">
      </gmap-marker>

      <gmap-info-window
        :options="infoOptions"
        :position="infoWindowPos"
        :opened="infoWinOpen"
        @closeclick="infoWinOpen=false"
      >
        <card inMap />
      </gmap-info-window>

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
        zoomControl: true,
        mapTypeControl: false,
        scaleControl: true,
        streetViewControl: false,
        rotateControl: false,
        fullscreenControl: false
      },
      center: {
        lat: 52.511950,
        lng: 6.089625
      },
      map: null,
      infoContent: '',
      infoWindowPos: {
        lat: 0,
        lng: 0
      },
      infoWinOpen: false,
      currentMidx: null,
      //optional: offset infowindow so it visually sits nicely on top of our marker
      infoOptions: {
        pixelOffset: {
          width: -10,
          height: -45
        }
      },
      markers: [{
          name: "House of Aleida Greve",
          description: "description 1",
          date_build: "",
          position: {
            lat: 40.711631,
            lng: -74.006641
          },
        },
        {
          name: "House of Potgieter",
          description: "description 2",
          date_build: "",
          position: {
            lat: 40.720840, 
            lng: -74.010571
          }
        },
        {
          name: "House of Johannes Cele",
          description: "description 3",
          date_build: "",
          position: {
            lat: 40.732740,
            lng: -74.010571
          }
        },
      ],
    };
  },
  mounted() {
    //set bounds of the map
    this.$refs.gmap.$mapPromise.then((map) => {
      const bounds = new google.maps.LatLngBounds()
      for (let m of this.markers) {
        bounds.extend(m.position)
      }
      map.fitBounds(bounds);
    });
  },
  methods: {
    toggleInfoWindow: function (marker, idx) {
      this.infoWindowPos = marker.position;

      //check if its the same marker that was selected if yes toggle
      if (this.currentMidx == idx) {
        this.infoWinOpen = !this.infoWinOpen;
      }
      //if different marker set infowindow to open and reset current marker index
      else {
        this.infoWinOpen = true;
        this.currentMidx = idx;
      }
    }
  }
};
</script>