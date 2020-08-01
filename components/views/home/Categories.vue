<template>
  <v-container id="categories">
    <div class="categories-container">
      <specialities-slider />
      <div class="inputs-container">
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
      </div>
    </div>
  </v-container>
</template>

<script>
import SpecialitiesSlider from "@/components/SpecialitiesSlider";
export default {
  components: { SpecialitiesSlider },
  data: () => ({
    range: [200, 800],
    treatments: [],
  }),
};
</script>

<style scoped lang="scss">
#categories {
  position: relative;
  z-index: 10;
  .categories-container {
    background-color: #f5f5f5;
    margin-top: 0;
    transform: translateY(-20px);
  }
  .inputs-container {
    padding: 0 15px;
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
}
</style>