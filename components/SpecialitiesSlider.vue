<template>
  <div class="specialities-body" :class="{'noMargin': $route.name !== 'index'}">
    <div @click="slidePrev()" class="slider-controller left-controller">
      <i class="fa fa-chevron-left"></i>
    </div>
    <VueSlickCarousel class="slider" ref="carousel" v-bind="options">
      <category
        v-for="(item,index) in specialities"
        :key="index"
        :img="item.img"
        :title="item.title"
      />
    </VueSlickCarousel>
    <div @click="slideNext()" class="slider-controller right-controller">
      <i class="fa fa-chevron-right"></i>
    </div>
  </div>
</template>

<script>
import { mapState } from "vuex";
import Category from "@/components/Category";
export default {
  data() {
    return {
      //data list [array]
      range: [125, 587],
      //Slider configuration [obj]
      options: {
        slidesToShow: 14,
        arrows: false,
        autoplay: false,
        responsive: [
          {
            breakpoint: 1800,
            settings: {
              slidesToShow: 12,
            },
          },
          {
            breakpoint: 1500,
            settings: {
              slidesToShow: 9,
            },
          },
          {
            breakpoint: 1400,
            settings: {
              slidesToShow: 8,
            },
          },
          {
            breakpoint: 1300,
            settings: {
              slidesToShow: 7,
            },
          },
          {
            breakpoint: 800,
            settings: {
              slidesToShow: 5,
            },
          },
          {
            breakpoint: 600,
            settings: {
              slidesToShow: 3,
            },
          },
          {
            breakpoint: 480,
            settings: {
              slidesToShow: 1,
            },
          },
        ],
      },
    };
  },
  methods: {
    slideNext() {
      this.$refs.carousel.next();
    },
    slidePrev() {
      this.$refs.carousel.prev();
    },
  },
  computed: {
    ...mapState({
      specialities: ({ Speciality }) => Speciality.all,
    }),
  },
  components: {
    Category,
  },
};
</script>

<style scoped lang="scss">
.specialities-body {
  position: relative;
  transform: translateY(-15px);
  margin: 10px 15px;
  background-color: white;
  z-index: 10;
  border-radius: 5px;
  overflow: hidden;
  border: 1px solid rgb(226, 226, 226);
  &.noMargin {
    margin: 0;
  }
  .slider {
    display: block;
    padding: 0 50px;
  }
  .slider-controller {
    height: 100%;
    background: #f5f5f5;
    display: flex;
    align-items: center;
    padding: 1.2rem;
    font-size: 1.2rem;
    color: #00cae9;
    position: absolute;
    z-index: 1;
    cursor: pointer;
    &.right-controller {
      right: 0;
      top: 0;
    }
  }
}
</style>