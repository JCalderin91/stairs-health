<template>
  <v-container>
    <h1 class="title py-3">Premium Features</h1>
    <v-row>
      <v-col :md="3">
        <v-hover v-slot:default="{ hover }">
          <v-card class="card">
            <v-img
              class="white--text align-end"
              gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
              height="170px"
              :src="require('~/assets/image/feature-1.png')"
            >
              <v-expand-transition>
                <div
                  v-if="hover"
                  class="d-flex transition-fast-in-fast-out v-card--reveal display-3 white--text"
                  style="height: 100%;"
                ></div>
              </v-expand-transition>
              <v-card-title>Cash payment discount</v-card-title>
            </v-img>
          </v-card>
        </v-hover>
      </v-col>

      <v-col :md="3">
        <v-hover v-slot:default="{ hover }">
          <v-card class="card">
            <v-img
              class="white--text align-end"
              gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
              height="170px"
              :src="require('~/assets/image/feature-2.png')"
            >
              <v-expand-transition>
                <div
                  v-if="hover"
                  class="d-flex transition-fast-in-fast-out v-card--reveal display-3 white--text"
                  style="height: 100%;"
                ></div>
              </v-expand-transition>
              <v-card-title>Patient loyalty discount</v-card-title>
            </v-img>
          </v-card>
        </v-hover>
      </v-col>

      <v-col :md="3">
        <v-hover v-slot:default="{ hover }">
          <v-card class="card">
            <v-img
              class="white--text align-end"
              gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
              height="170px"
              :src="require('~/assets/image/feature-3.png')"
            >
              <v-expand-transition>
                <div
                  v-if="hover"
                  class="d-flex transition-fast-in-fast-out v-card--reveal display-3 white--text"
                  style="height: 100%;"
                ></div>
              </v-expand-transition>
              <v-card-title>Bundles</v-card-title>
            </v-img>
          </v-card>
        </v-hover>
      </v-col>

      <v-col :md="3">
        <v-hover v-slot:default="{ hover }">
          <v-card class="card">
            <v-img
              class="white--text align-end"
              gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
              height="170px"
              :src="require('~/assets/image/feature-4.png')"
            >
              <v-expand-transition>
                <div
                  v-if="hover"
                  class="d-flex transition-fast-in-fast-out v-card--reveal display-3 white--text"
                  style="height: 100%;"
                ></div>
              </v-expand-transition>
              <v-card-title>PCP Televisit</v-card-title>
            </v-img>
          </v-card>
        </v-hover>
      </v-col>
    </v-row>
  </v-container>
</template>

<style scoped lang="scss">
.title {
  color: #ffe600;
  text-align: center;
  font-size: 2.2rem !important;
  font-weight: bold;
  text-transform: uppercase;
}

.v-card--reveal {
  background-color: #00cae981;
  align-items: flex-end;
  bottom: 0;
  justify-content: flex-start;
  position: absolute;
  width: 100%;
  z-index: -1;
}
</style>