<template>
  <v-app dark>
    <v-container class="text-center">
      <h3 class="error-code primary-text">{{error.statusCode}}</h3>
      <h1 v-if="error.statusCode === 404">{{ pageNotFound }}</h1>
      <h1 v-else>{{ otherError }}</h1>
      <v-btn small elevation="2" color="primary" class="mt-2">Go to gome</v-btn>
    </v-container>
  </v-app>
</template>

<script>
export default {
  layout: "empty",
  props: {
    error: {
      type: Object,
      default: null,
    },
  },
  data() {
    return {
      pageNotFound: "404 Not Found",
      otherError: "An error occurred",
    };
  },
  head() {
    const title =
      this.error.statusCode === 404 ? this.pageNotFound : this.otherError;
    return {
      title,
    };
  },
};
</script>

<style scoped>
.error-code {
  font-size: 4rem;
  margin-bottom: 1rem;
}
</style>
