<template>
  <Navbar :theme="theme" :toggleTheme="toggleTheme" />
  <div class="container d-flex justify-content-center">
    <Gallery :width="3" :height="4" />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Gallery from "./components/Gallery.vue";
import Navbar from "./components/Navbar.vue";

export default defineComponent({
  name: "App",
  components: {
    Gallery,
    Navbar,
  },
  data() {
    return {
      theme: "dark",
    };
  },
  methods: {
    toggleTheme() {
      this.theme = this.theme === "dark" ? "light" : "dark";
    },
  },
});
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  overflow-y: scroll;
  background-color: rgb(45, 41, 53);
  min-width: 100vw;
  min-height: 100vh;
}
</style>
