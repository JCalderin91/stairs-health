<template>
  <v-container id="treatment">
    <div class="separador"></div>
    <v-row>
      <v-col :md="6">
        <h2>Treatment name</h2>
        <p>Treatment description associated cost for this service</p>
      </v-col>
      <v-col :md="6" class="d-flex align-center justify-end">
        <div class="d-flex justify-end aligns-center">
          <sh-button :to="{name:'compare'}" invert img="Arrows.svg">Compare providers</sh-button>
        </div>
      </v-col>
    </v-row>
    <div class="separador"></div>
  </v-container>
</template>

<style scoped lang="scss">
#treatment {
  margin-bottom: 20px;
}
</style>