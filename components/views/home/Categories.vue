<template>
  <v-container id="categories">
    <div class="categories-container">
      <specialities-slider />
      <div class="inputs-container">
        <v-row>
          <v-col :md="4">
            <v-text-field
              outlined
              rounded
              append-icon="mdi-magnify"
              placeholder="Search"
              class="mx-10"
            ></v-text-field>
          </v-col>
          <v-col :md="4">
            <v-text-field
              outlined
              rounded
              append-icon="mdi-map-marker"
              placeholder="Zip code or City"
              class="mx-10"
            ></v-text-field>
          </v-col>
          <v-col :md="4">
            <v-range-slider
              label="Price range"
              class="mt-5 mr-10"
              v-model="range"
              min="100"
              max="1000"
              thumb-label="always"
              :thumb-size="24"
            ></v-range-slider>
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
    range: [100, 1000],
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
}
</style>