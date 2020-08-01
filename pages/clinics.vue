<template>
  <div>
    <v-container class="py-0">
      <specialities-slider />
    </v-container>
    <section class="filter-container pt-3">
      <v-container class="py-0">
        <v-row class="mt-5">
          <v-col :md="3">
            <v-menu :close-on-content-click="false" bottom offset-y>
              <template v-slot:activator="{ on: menu, attrs }">
                <v-btn
                  rounded
                  x-large
                  block
                  color="primary"
                  v-bind="attrs"
                  v-on="{ ...menu }"
                >Chose your insurance</v-btn>
              </template>
              <v-card>
                <choose-insurance />
              </v-card>
            </v-menu>
          </v-col>
          <v-col :md="3">
            <v-autocomplete
              :items="treatments"
              outlined
              chips
              rounded
              small-chips
              background-color="white"
              label="Treatments"
            ></v-autocomplete>
          </v-col>
          <v-col :md="3">
            <v-text-field
              outlined
              rounded
              background-color="white"
              append-icon="mdi-map-marker"
              placeholder="Zip code or City"
            ></v-text-field>
          </v-col>
          <v-col :md="3">
            <div class="custom-range-slider">
              <v-range-slider
                class="mt-5"
                v-model="range"
                min="100"
                max="1000"
                thumb-label="always"
                :thumb-size="20"
              >
                <template v-slot:thumb-label></template>
              </v-range-slider>
              <span class="span-label min">Min</span>
              <span class="span-label label">Price</span>
              <span class="span-label max">Max</span>
            </div>
          </v-col>
        </v-row>
      </v-container>
    </section>
    <v-container>
      <v-row>
        <v-col :md="mapCol" class="mapContainer py-0">
          <div class="mapa static-map">
            <map-specialities id="map" />
          </div>
        </v-col>
        <v-col v-if="mapCol === 3" :md="9" class="specialities-container---- py-0">
          <v-col cols="12">
            <v-chip close color="primary">Insurance 2 - Plan 4</v-chip>
            <v-chip close color="primary">Treatmen premium</v-chip>
            <v-chip close color="primary">New York City</v-chip>
            <v-chip close color="primary">{{range[0]}}$ - {{range[1]}}$</v-chip>
          </v-col>
          <v-col cols="12" class="py-0 d-flex justify-space-between align-center">
            <h6>Showing 100 results</h6>
            <div class="selector">
              <v-icon color>mdi-format-list-bulleted</v-icon>
              <v-switch class="ml-4" v-model="viewType" inset></v-switch>
              <v-icon color>mdi-view-grid</v-icon>
            </div>
          </v-col>
          <v-row id="specialities-container">
            <v-col class="pt-0" :md="viewType?'4':'12'" v-for="i in 15" :key="i">
              <router-link tag="div" :to="{name:'clinic'}">
                <specialities-card v-if="viewType" />
                <specialities-list v-else />
              </router-link>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import SpecialitiesSlider from "@/components/SpecialitiesSlider";
import SpecialitiesCard from "@/components/Card";
import SpecialitiesList from "@/components/List";
import MapSpecialities from "@/components/Map";
import ChooseInsurance from "@/components/ChooseInsurance";
export default {
  components: {
    SpecialitiesSlider,
    SpecialitiesCard,
    SpecialitiesList,
    MapSpecialities,
    ChooseInsurance,
  },
  data: () => ({
    mapCol: 3,
    fixed: "",
    range: [200, 800],
    viewType: false,
    treatments: [],
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
.filter-container {
  background-color: #f5f4f5;
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
.selector {
  display: flex;
}
.custom-range-slider {
  position: relative;
  .span-label {
    position: absolute;
    top: 20px;
    &.min {
      color: #00cae9;
    }
    &.max {
      right: 0;
      color: #00cae9;
    }
    &.label {
      left: 50%;
      transform: translateX(-50%);
      color: rgb(158, 158, 158);
    }
  }
}

.specialities-container {
  height: 100vh;
  overflow-y: scroll;
}
</style>