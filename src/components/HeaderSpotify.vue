<template>
  <div class="container-header">
    <div>
      <img src="../assets/spotify-logo-2.png" alt="logo-spotify" />
    </div>
  </div>
</template>

<script>
export default {
  name: "HeaderSpotify",
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "src/variabili.scss";
.container-header {
  padding: 10px 15px;
  background-color: $bg-secondary;
  div {
    width: 50px;
    img {
      width: 100%;
    }
  }
}
</style>
