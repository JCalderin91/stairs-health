<template>
  <v-parallax dark :src="require('~/assets/image/parallax.png')" height="350">
    <v-container>
      <v-row align="center" justify="center">
        <v-col :md="12" class="d-flex justify-start" cols="12">
          <div class="box registered">
            <h1 class="display-1 font-weight-thin mb-4">Registered</h1>
            <h5 class="subheading">Lorem ipsum dolor sit amet, consectetur adipisicing elit.</h5>
          </div>

          <div class="box premium">
            <h1 class="display-1 font-weight-thin mb-4">Premium</h1>
            <h5 class="subheading">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quae.</h5>
          </div>
        </v-col>
      </v-row>
    </v-container>
  </v-parallax>
</template>

<style scoped lang="scss">
.box {
  padding: 3rem 2.5rem;
  border-radius: 8px;
  margin: 0 15px;
  width: 300px;

  &.registered {
    background-color: #00cae9ee;
  }

  &.premium {
    background-color: #ffe600ee;
    color: #555;
  }
}
</style>