<template>
  <v-container id="compare" class="pa-0 my-6">
    <v-row>
      <v-col md="6" class="px-5">
        <clinic />
      </v-col>
      <v-col md="6" class="px-5 right-panel">
        <v-card class="card-base" outlined v-if="compare">
          <clinic />
        </v-card>
        <v-row v-else>
          <v-row>
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
                label="Treatments"
              ></v-autocomplete>
            </v-col>
            <v-col :md="3">
              <v-text-field
                outlined
                rounded
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
          <v-row class="px-5">
            <v-col @click="compare = !compare" md="6" v-for="i in 6" :key="i">
              <card-speciality />
            </v-col>
          </v-row>
        </v-row>
      </v-col>
      <v-col v-if="compare" md="12" class="text-center">
        <v-btn @click="compare = !compare" color="primary" class="px-10 py-6" rounded>KEEP LOOKING</v-btn>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import Clinic from "@/components/Clinic";
import CardSpeciality from "@/components/Card";
export default {
  components: {
    Clinic,
    CardSpeciality,
  },
  data: () => ({
    compare: false,
  }),
};
</script>

<style lang="scss" scoped>
#compare {
  .card-base {
    border: none !important;
    background: transparent;
  }

  position: relative;

  &::before {
    content: "";
    position: absolute;
    top: -28px;
    left: 50%;
    min-height: 100vh;
    height: 120%;
    width: 50vw;
    z-index: 0;
    background-color: #f5f5f5;
  }
}
</style>