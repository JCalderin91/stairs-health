<template>
  <div>
    <!-- <hero /> -->
    <!-- <categories /> -->
    <clinics />
    <features />
    <parallax />
  </div>
</template>
<script>
// import Hero from "~/components/views/home/Hero";
// import Categories from '~/components/views/home/Categories'
import Clinics from "~/components/views/home/Clinics";
import Features from "~/components/views/home/Features";
import Parallax from "~/components/views/home/Parallax";
export default {
  components: {
    // Hero,
    // Categories,
    Clinics,
    Features,
    Parallax,
  },
  data() {
    return {};
  },
};
</script>