<template>
  <div id="category" :class="{'hover': !noHover}">
    <div class="image-container" :class="{'noHome': noHome}">
      <img class="image" :src="getImg()" :alt="title" />
    </div>
    <span v-if="!noText" class="text">{{title}}</span>
  </div>
</template>

<script>
export default {
  name: "category",
  props: {
    title: {
      type: String,
    },
    img: {
      type: String,
      required: true,
    },
    active: {
      type: Boolean,
      default: false,
    },
    noText: {
      type: Boolean,
      default: false,
    },
    noHover: {
      type: Boolean,
      default: false,
    },
  },
  data: () => ({
    //
  }),
  methods: {
    getImg() {
      return require("@/assets/image/" + this.img);
    },
  },
  computed: {
    noHome() {
      return this.$route.name !== "home" && this.$route.name !== "clinics";
    },
  },
};
</script>
<style scoped lang="scss">
#category {
  display: flex;
  flex-direction: column;
  margin: 20px auto 25px auto;
  text-align: center;
  transition: all 0.3s ease-in-out;
  &.hover {
    cursor: pointer;
    &:hover {
      .image-container {
        border: 2px solid #00cae9;
        background-color: #00cae9;
        .image {
          filter: invert(1);
        }
      }
    }
  }
  .text {
    color: #000;
    margin-top: 16px;
    font-size: 12px;
  }
  .image-container {
    height: 80px;
    width: 80px;
    padding: 20px;
    border-radius: 50%;
    border: 2px solid #888;
    margin: 0 auto;
    transition: all 0.3s ease-in-out;
    &.noHome {
      height: 100px !important;
      width: 100px !important;
    }
    .image {
      width: 100%;
      height: 100%;
      transition: all 0.3s ease-in-out;
    }
  }
}
</style>
