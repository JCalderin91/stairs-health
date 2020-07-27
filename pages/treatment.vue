<template>
  <v-container class="my-6">
    <treatment v-for="i in 3" :key="i" />
  </v-container>
</template>

<script>
import Treatment from "@/components/Treatment";
export default {
  components: { Treatment },
};
</script>