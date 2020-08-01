<template>
  <v-container>
    <v-row>
      <v-col :md="4">
        <v-img class="main-img" :src="require('@/assets/image/hero.png')" height="250"></v-img>
      </v-col>
      <v-col :md="8" class="pt-10">
        <h1 class="title-clinic">Clinic Domenic</h1>
        <information />
        <div class="button d-flex justify-end">
          <sh-button :to="{name:'your-spot'}" img="calendario-3.svg">
            Save
            <b class="ml-1">your Spot</b>
          </sh-button>
        </div>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import Information from "@/components/Information";
export default {
  components: {
    Information,
  },
};
</script>

<style scoped lang="scss">
.title-clinic {
  font-weight: 100;
  font-size: 2.5rem;
}
</style>