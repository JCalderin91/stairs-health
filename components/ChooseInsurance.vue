<template>
  <v-card class="insurance-card px-5 py-2">
    <v-card-text class="d-flex justify-space-between">
      <v-btn @click="step = 1" small rounded class="primary">
        Insurance carrier
        <v-icon right>mdi-check-circle-outline</v-icon>
      </v-btn>

      <v-btn :disabled="step!==2" small rounded :class="{'primary': step==2}">
        Insurance plan
        <v-icon v-if="step==2" right>mdi-check-circle-outline</v-icon>
      </v-btn>
    </v-card-text>
    <v-card-text class="py-0">
      <v-text-field label="Search" append-icon="mdi-magnify" outlined dense rounded></v-text-field>
    </v-card-text>
    <v-card-text class="insurances">
      <template v-if="step==1">
        <div v-for="(item, index) in items" :key="index">
          <h1 class="primary--text mb-2">{{item}}</h1>
          <h4
            class="insurance"
            @click="choiceCarrier(r)"
            v-for="(r, key) in randomValue"
            :key="key"
          >Insurance {{ r }}</h4>
          <v-divider class="ma-4"></v-divider>
        </div>
      </template>
      <template v-else>
        <h4
          class="plan"
          @click="choicePlan(r)"
          v-for="(r, key) in randomItems(15,5)"
          :key="key"
        >Plan {{ r }}</h4>
      </template>
    </v-card-text>
  </v-card>
</template>
<script>
export default {
  data: () => ({
    items: ["#", "A", "B", "D", "G"],
    step: 1,
    randomValue: null,
    insurance: {
      carrier: null,
      plan: null,
    },
  }),
  methods: {
    randomItems(min = 1, max = 6) {
      return Math.ceil(Math.random() * (max - min) + min);
    },
    choiceCarrier(num) {
      this.step = 2;
      this.carrier = `Insurance ${num}`;
    },
    choicePlan(num) {
      this.plan = `Plan ${num}`;
    },
  },
  mounted() {
    this.randomValue = this.randomItems();
  },
};
</script>
<style lang="scss" scoped>
.insurance-card {
  min-width: 500px;
  .insurances {
    max-height: 400px;
    overflow-y: scroll;
    .insurance {
      cursor: pointer;
    }
  }
  .plan {
    cursor: pointer;
  }
}
</style>