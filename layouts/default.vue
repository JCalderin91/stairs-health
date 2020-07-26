<template>
  <v-app>
    <main-menu @toggleDialog="dialog = $event" />
    <nuxt />
    <end-page />
    <v-dialog v-model="dialog" max-width="350">
      <v-card>
        <login />
      </v-card>
    </v-dialog>
  </v-app>
</template>

<script>
import MainMenu from "@/components/Menu";
import EndPage from "@/components/EndPage";
import Login from "@/components/views/auth/Login";
export default {
  components: {
    MainMenu,
    EndPage,
    Login,
  },
  data() {
    return {
      dialog: false,
    };
  },
};
</script>
