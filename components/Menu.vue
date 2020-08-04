<template>
  <v-app-bar id="menu" color="primary" app>
    <div class="container d-flex align-center">
      <v-toolbar-title class="container-logo">
        <nuxt-link tag="a" :to="'/'">
          <img class="logo-app" src="@/assets/logo-white.png" alt />
        </nuxt-link>
      </v-toolbar-title>
      <v-spacer></v-spacer>

      <div class="menu-nav-bar">
        <span>How it Works</span>
        <span>Explore Savings</span>
        <span>Become a Member</span>
        <span>For Providers</span>
        <span>Contact Us</span>
      </div>

      <v-spacer></v-spacer>

      <div class="menu-nav-bar">
        <span @click="login">Login</span>
        <span class="layer">|</span>
        <span>Register</span>
      </div>
    </div>
  </v-app-bar>
</template>

<script>
export default {
  data: () => ({
    //
  }),
  computed: {
    home() {
      return this.$route.name !== "home";
    },
  },
  methods: {
    login() {
      this.$emit("toggleDialog", true);
    },
  },
};
</script>

<style scoped lang="scss">
#menu {
  z-index: 30;

  .container {
    height: 100%;

    .container-logo,
    .logo-app {
      height: 100%;
    }

    .menu-nav-bar {
      span {
        cursor: pointer;
        padding: 3px 5px;
        margin: 0 3px;
        color: white;
        position: relative;

        &.layer::before {
          content: "";
          background: #04d5f5;
          position: absolute;
          top: -19px;
          left: 0px;
          height: 64px;
          width: 100vw;
        }
      }
    }
  }
}
</style>
