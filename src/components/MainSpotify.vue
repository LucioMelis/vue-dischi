<template>
  <div class="container-main">
    <div class="container-card">
      <CardDisc />
    </div>
  </div>
</template>

<script>
import CardDisc from "../components/CardDisc.vue";

export default {
  name: "MainSpotify",
  components: {
    CardDisc,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "src/variabili.scss";
</style>
