<template>
  <div>
    <Loader v-if="loaderEnabled" v-bind:logo="loaderLogo"></Loader>
    <Navbar />
    <router-view></router-view>
  </div>
</template>

<style lang="scss">
// 3rd party plugins css

// Main demo style scss

// RTL css
/*@import "assets/css/style.vue.rtl";*/

// skins
</style>
<script>
import Navbar from "@/layouts/navbar";
import { mapGetters } from "vuex";
import Loader from "@/components/Loader.vue";
import HtmlClass from "@/common/htmlclass.service";

import {
  ADD_BODY_CLASSNAME,
  REMOVE_BODY_CLASSNAME
} from "@/store/htmlclass.module.js";

export default {
  name: "talabat",
  beforeMount() {
    // show page loading
    this.$store.dispatch(ADD_BODY_CLASSNAME, "kt-page--loading");

    // initialize html element classes
    HtmlClass.init();
  },
  mounted() {
    // Simulate the delay page loading
    setTimeout(() => {
      // Remove page loader after some time
      this.$store.dispatch(REMOVE_BODY_CLASSNAME, "kt-page--loading");
    }, 4000);
  },
  components: {
    Navbar,
    Loader,
  },
  computed: {
    ...mapGetters([
      "pageTitle",
      "layoutConfig"
    ]),

    /**
     * Check if the page laoder is enabled
     * @returns {boolean}
     */
    loaderEnabled() {
      return !!this.layoutConfig("loader.enabled");
    },

    /**
     * Page loader logo image using require() function
     * @returns {string}
     */
    loaderLogo() {
      return process.env.BASE_URL + this.layoutConfig("loader.logo");
    },

  }

  
};
</script>
