<template>
  <Navbar />
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
}
</style>
