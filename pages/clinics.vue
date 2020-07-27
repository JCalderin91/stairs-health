<template>
  <v-container>
    <specialities-slider />
    <v-row>
      <v-col :md="3">
        <v-text-field outlined rounded placeholder="Speciality" class="mx-10"></v-text-field>
      </v-col>
      <v-col :md="3">
        <v-text-field outlined rounded placeholder="Treatment" class="mx-10"></v-text-field>
      </v-col>
      <v-col :md="3">
        <v-text-field
          outlined
          rounded
          append-icon="mdi-map-marker"
          placeholder="Zip code or City"
          class="mx-10"
        ></v-text-field>
      </v-col>
      <v-col :md="3">
        <v-range-slider
          label="Price range"
          class="mt-5"
          v-model="range"
          min="100"
          max="1000"
          thumb-label="always"
          :thumb-size="24"
        ></v-range-slider>
      </v-col>
    </v-row>

    <v-row>
      <v-col :md="mapCol" class="mapContainer">
        <div class="mapa static-map">
          <map-specialities id="map" />
        </div>
      </v-col>
      <v-col v-if="mapCol === 3" :md="9" class="specialities-container----">
        <v-row id="specialities-container">
          <v-col class="pt-0" md="4" v-for="i in 15" :key="i">
            <router-link tag="div" :to="{name:'clinic'}">
              <specialities-card />
            </router-link>
          </v-col>
        </v-row>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import SpecialitiesSlider from "@/components/SpecialitiesSlider";
import SpecialitiesCard from "@/components/Card";
import MapSpecialities from "@/components/Map";
export default {
  components: {
    SpecialitiesSlider,
    SpecialitiesCard,
    MapSpecialities,
  },
  data: () => ({
    mapCol: 3,
    fixed: "",
    range: [100, 1000],
  }),
  methods: {
    toogleMap() {
      this.mapCol = this.mapCol === 3 ? 12 : 3;
    },
  },
};
</script>

<style scoped lang="scss">
.indicator {
  position: fixed;
  bottom: 12px;
  right: 12px;
  z-index: 9999;
}

.mapContainer {
  .static-map {
    position: sticky;
    top: 64px;
    height: calc(100vh - 61px);
  }

  #floor {
    position: absolute;
    bottom: 0;
    width: 100%;
    height: 1px;
    background-color: #000;
  }

  .expand-button {
    position: absolute;
    top: 0;
    right: 0;
    background-color: #00cae9;
    padding: 0.5rem 1.5rem;
    color: white;
    border-radius: 0 0 0 13px;
    z-index: 10;
    cursor: pointer;

    .expand-text {
      font-size: 0.9rem;
      font-weight: bold;
    }

    .expand-icon {
      font-size: 0.8rem;
      margin-left: 5px;
      transform: translateY(1px);
    }

    .collapse-icon {
      font-size: 0.8rem;
      margin-right: 5px;
      transform: translateY(1px);
    }
  }
}

.specialities-container {
  height: 100vh;
  overflow-y: scroll;
}
</style>