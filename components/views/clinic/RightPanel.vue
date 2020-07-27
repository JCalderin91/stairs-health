<template>
  <div>
    <div class="tabs">
      <div @click="panel=1" class="tabs-item" :class="{'active': panel===1}">Treatments & Price list</div>
      <div @click="panel=2" class="tabs-item" :class="{'active': panel===2}">Direct contact</div>
    </div>
    <br />
    <transition name="fade" mode="out-in">
      <speciality-list v-if="panel===1" key="speciality-list" />
      <div v-else key="map">
        <div class="map-contact">
          <map-contact />
        </div>
        <br />
        <information class="px-2" />
        <br />
        <div class="icons">
          <a href>
            <i class="fa fa-envelope"></i>
          </a>
          <a href>
            <i class="fa fa-globe"></i>
          </a>
          <a href>
            <i class="fa fa-instagram"></i>
          </a>
          <a href>
            <i class="fa fa-twitter"></i>
          </a>
          <a href>
            <i class="fa fa-facebook"></i>
          </a>
        </div>
        <br />
        <div class="d-flex justify-center">
          <sh-button invert text="Call Us" img="phone.svg" />
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
import Information from "@/components/Information";
import ShButton from "@/components/ShButton";
import SpecialityList from "@/components/SpecialityList";
import MapContact from "@/components/MapContact";

export default {
  components: {
    Information,
    ShButton,
    SpecialityList,
    MapContact,
  },
  data: () => ({
    panel: 1,
  }),
  computed: {
    filterCategories() {
      return this.speciality.length === 0
        ? this.categories
        : this.categories.filter((category) =>
            category.title.toUpperCase().includes(this.speciality.toUpperCase())
          );
    },
  },
};
</script>

<style scoped lang="scss">
.map-contact {
  height: 200px;
}
.tabs {
  display: flex;
  justify-content: space-between;
  .tabs-item {
    cursor: pointer;
    font-size: 1.3rem;
    padding: 8px 20px;
    &.active {
      border-bottom: 3px solid #00cae9;
    }
  }
}
.icons {
  text-align: center;
  font-size: 1.5rem;
  a {
    transition: all 0.2s ease-in-out;
    margin: 0rem 0.5rem;
    color: #123959;
    padding: 0.1rem 0.5rem;
    &:hover {
      color: #00cae9;
    }
  }
}
</style>