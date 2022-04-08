<template>
  <div id="app">
    <HeaderSpotify />
    <MainSpotify />
  </div>
</template>

<script>
import HeaderSpotify from "./components/HeaderSpotify.vue";
import MainSpotify from "./components/MainSpotify.vue";

export default {
  name: "App",
  components: {
    HeaderSpotify,
    MainSpotify,
  },
};
</script>

<style lang="scss">
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
}
</style>
