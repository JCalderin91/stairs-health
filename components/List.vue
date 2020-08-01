<template>
  <v-card id="clinic-list" class="mb-5">
    <v-row>
      <v-col :md="3" class="pl-3 pa-0">
        <v-img
          class="image-clinic"
          gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.4)"
          :src="require('~/assets/image/0.png')"
        ></v-img>
      </v-col>
      <v-col :md="4">
        <h2 class="title-clinic mb-3">
          Clinic Domenic
          <v-icon>mdi-heart-outline</v-icon>
        </h2>
        <p class="mb-1">867 Greenholt Parkways Apt. 670, New York City.</p>
        <p class="mb-1">www.clinicdomenic.com</p>
        <p class="mb-1">10 am - 10 pm</p>
        <p class="mb-1">603 77 51 38</p>
      </v-col>
      <div class="badge">
        <div class="price">$ 200</div>
        <div class="text">Standar Charges</div>
      </div>
    </v-row>
  </v-card>
</template>

<script>
export default {
  props: {
    inMap: {
      type: Boolean,
      default: false,
    },
  },
};
</script>

<style scoped lang="scss">
#clinic-list {
  overflow: hidden;
  .image-clinic {
    height: 100%;
  }
  .badge {
    position: absolute;
    top: 0;
    right: 0;
    padding: 5px 20px;
    border-radius: 0 0 0 10px;
    background-color: #00cae9ee;

    .price {
      color: white;
      font-weight: bold;
      font-size: 18px;
    }

    .text {
      font-size: 10px;
      color: white;
    }
  }
}
</style>
