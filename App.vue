<script>
import * as d3 from "https://cdn.skypack.dev/d3@7";
import AOS from "aos";
import "aos/dist/aos.css";

import Vue from "vue";
import { BootstrapVue, IconsPlugin } from "bootstrap-vue";

// Import Bootstrap and BootstrapVue CSS files (order is important)
import "bootstrap/dist/css/bootstrap.css";
import "bootstrap-vue/dist/bootstrap-vue.css";

// Make BootstrapVue available throughout your project
Vue.use(BootstrapVue);
// Optionally install the BootstrapVue icon components plugin
Vue.use(IconsPlugin);

import Home from "./components/Home.vue";
export default {
  name: "App",
  components: { Home, },
  data() {
    return {
      home: true,
      other: false,
    };
  },
  mounted() {},
  methods: {
    update_page(name) {
      this.target_page = name;
      if (this.target_page == "Home") {
        this.home = true;

        setTimeout(() => {
          AOS.refresh();
        }, 500);
        AOS.init({ offset: 130, duration: 1000 });

        this.other = false;
      } else if (this.target_page == "Other") {
        this.other = true;
        this.home = false;
      }
    },
  },
  watch: {},
};
</script>


<template >
<span>
 <b-navbar type="dark" variant="dark" id="navbar">
      <b-navbar-nav>
        <b-nav-item  @click="update_page('Home')">Home</b-nav-item>
        <b-nav-item @click="update_page('Other')">Altro</b-nav-item>
        <!-- Navbar dropdowns -->
      </b-navbar-nav>
      </b-navbar>
    <div id="app">

    <Home v-if="home"></Home>

    <div v-if="other" >other</div>
</div>
</span>
</template>

<style>
#app{
  align-self: start !important;
  display: block !important;
  width: 100% !important;
  padding:0% !important
}
#navbar {
	background-color: #009fe3;
	width: 100%;
	box-sizing: content-box;
	}
	
body {
  margin:0 !important;
	width: 100% !important;
  display:block !important;
}
</style>
