<template>
  <div id="home">
    <section class="hero">
      <img src="@/assets/image/hero.png" alt class="img-hero" />
      <transition name="up">
        <img v-if="wave" src="@/assets/image/wave.svg" alt class="img-hero-wave" />
      </transition>
      <div class="container">
        <v-row class="container-hero" align="center">
          <v-col :md="6" class="d-flex align-center flex-column">
            <img class="img-logo" height="150" src="@/assets/image/logo-full-white.png" alt />
            <h4 class="py-5 up white--text">{{texts[showBanner].title}}</h4>
            <ul class="up white--text become-list">
              <li v-for="(item, key) in texts[showBanner].items" :key="key">
                <i class="fa fa-circle"></i>
                {{item}}
              </li>
            </ul>
          </v-col>
          <v-col :md="6">
            <div style="width:100%;margin:20px auto;height:500px">
              <VueSlickCarousel ref="carousel" @afterChange="afterChange($event)" v-bind="options">
                <div class="img-wrapper">
                  <img class="img-phone" src="@/assets/image/banner-gif-1.png" alt />
                </div>
                <div class="img-wrapper">
                  <img class="img-phone" src="@/assets/image/banner-gif-2.png" alt />
                </div>
                <div class="img-wrapper">
                  <img class="img-phone" src="@/assets/image/banner-gif-3.png" alt />
                </div>
              </VueSlickCarousel>
            </div>
          </v-col>
          <v-col :sm="12" class="up">
            <v-container>
              <div class="social-icons">
                <a href="#">
                  <i class="fa fa-facebook"></i>
                </a>
                <a href="#">
                  <i class="fa fa-twitter"></i>
                </a>
                <a href="#">
                  <i class="fa fa-instagram"></i>
                </a>
                <a href="#">
                  <i class="fa fa-globe"></i>
                </a>
              </div>
            </v-container>
          </v-col>
          <v-col :sm="12" class="up d-flex justify-center">
            <div class="banner-dots">
              <div
                @click="setBanner(i-1)"
                :class="{'active': (i-1)===showBanner}"
                class="dot"
                v-for="i in 3"
                :key="i"
              ></div>
            </div>
          </v-col>
        </v-row>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      wave: false,
      showBanner: 0,
      options: {
        slidesToShow: 1,
        arrows: false,
        autoplay: true,
      },
      texts: [
        {
          title: "Want to know much a medical service costs?",
          items: [
            "Search and compare services costs.",
            "Search by location.",
            "Search by speciality, procedure or treatment.",
            "Compare prices.",
          ],
        },
        {
          title: "Find the best choice",
          items: [
            "Select the provider of your choice.",
            "Direct contact with your provider.",
            "Schedule your appointment through our app.",
            "Benefit  from providers discounts by shopping services through our tool.",
          ],
        },
        {
          title: "Become a Stairs menber",
          items: [
            "Get control of your healthcare in One Step.",
            "Multiple Telehealth visits every year.",
            "Your medical records saved in our system.",
            "We will guide you and help ypu find the best quality and cost-effective care.",
          ],
        },
      ],
    };
  },
  mounted() {
    this.wave = true;
  },
  methods: {
    setBanner(indx) {
      this.$refs.carousel.goTo(indx);
    },
    afterChange(slide) {
      this.showBanner = slide;
    },
  },
};
</script>

<style lang="scss" scoped>
.hero {
  position: relative;
  overflow: hidden;

  .img-hero {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 0;
    object-fit: cover;
  }

  .img-hero-wave {
    position: absolute;
    left: -10px;
    width: calc(100% + 10px);
    bottom: 0;
    z-index: 1;
  }

  .container-hero {
    height: 100%;

    .img-phone,
    .img-logo {
      z-index: 1;
    }
    .slick-slider {
      z-index: 2;
    }

    .img-phone {
      height: 100%;
    }

    .become-list {
      width: 435px;
      height: 180px;

      li {
        list-style: none;
        padding: 3px;
        margin: 3px 0;

        i {
          font-size: 0.8rem;
          margin-right: 10px;
        }
      }
    }
  }

  .up {
    z-index: 1;
  }

  .social-icons {
    a {
      padding: 5px 8px;

      i {
        color: white;
        font-size: 1.5rem;
      }
    }
  }

  .banner-dots {
    .dot {
      display: inline-block;
      height: 1rem;
      width: 1rem;
      background-color: #fff;
      border-radius: 50%;
      margin: 5px 8px;
      cursor: pointer;
      transition: all 0.3s ease-in-out;
      opacity: 0.7;

      &.active,
      &:hover {
        transform: scale(1.4);
        opacity: 1;
      }
    }
  }
}

.up-enter-active,
.up-leave-active {
  transition: all 1s ease-in-out;
}

.up-enter,
	.up-leave-to

	/* .up-leave-active below version 2.1.8 */ {
  transform: translateY(100%) rotate(-5deg);
}
</style>