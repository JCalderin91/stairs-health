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
            <v-col md="6">
              <v-text-field
                hide-details
                outlined
                rounded
                placeholder="Speciality"
                background-color="white"
                class="w-100 px-5"
              ></v-text-field>
            </v-col>
            <v-col md="6">
              <v-text-field
                hide-details
                outlined
                rounded
                placeholder="Treatment"
                background-color="white"
                class="w-100 px-5"
              ></v-text-field>
            </v-col>
            <v-col md="6">
              <v-text-field
                hide-details
                outlined
                rounded
                placeholder="Location"
                append-icon="mdi-map-marker"
                background-color="white"
                class="w-100 px-5"
              ></v-text-field>
            </v-col>
            <v-col md="6">
              <v-text-field
                hide-details
                outlined
                rounded
                placeholder="Price"
                append-icon="mdi-currency-usd"
                background-color="white"
                class="w-100 px-5"
              ></v-text-field>
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