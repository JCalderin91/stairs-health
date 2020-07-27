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
          <sh-button :to="{name:'your-spot'}" text="Save your Spot" img="calendario-3.svg" />
        </div>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import Information from "@/components/Information";
import ShButton from "@/components/ShButton";
export default {
  components: {
    Information,
    ShButton,
  },
};
</script>

<style scoped lang="scss">
.title-clinic {
  font-weight: 100;
  font-size: 2.5rem;
}
</style>