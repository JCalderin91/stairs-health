<template>
  <v-card id="card" :class="{'border': !inMap}">
    <v-img class="white--text align-end" height="200px" :src="require('~/assets/image/0.png')">
      <div class="badge">
        <div class="price">$ 200</div>
        <div class="text">Standar Charges</div>
      </div>
      <div class="main-title">Clinic Domenic</div>
    </v-img>
    <v-card-text class="text--primary">
      <h4>Treatment Mane</h4>
      <h5>Teeament descrioption</h5>
    </v-card-text>
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
#card {
  box-shadow: none;
  cursor: pointer;

  &.border {
    border: 1px solid rgb(226, 226, 226);
  }

  .text--primary {
    h4 {
      text-decoration: none;
    }
  }

  .badge {
    position: absolute;
    top: 0;
    right: 0;
    padding: 5px 20px;
    border-radius: 0 0 0 10px;
    background-color: #00cae9ee;

    .price {
      font-weight: bold;
      font-size: 18px;
    }

    .text {
      font-size: 10px;
      color: white;
    }
  }

  .main-title {
    color: white !important;
    position: absolute;
    left: 0.5rem;
    bottom: 0.5rem;
  }
}
</style>
