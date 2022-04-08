<template>
  <div class="container-main">
    <div v-if="disc.length > 0" class="container-card">
      <CardDisc v-for="(song, index) in disc" :key="index" :songdisc="song" />
    </div>
    <div v-else>Loading..</div>
  </div>
</template>

<script>
import CardDisc from "../components/CardDisc.vue";
import axios from "axios";

export default {
  name: "MainSpotify",
  components: {
    CardDisc,
  },
  data() {
    return {
      disc: [],
    };
  },
  mounted() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((response) => {
        this.disc = response.data.response;
        // console.log(this.disc);
        console.log(this.disc[0]);
      });
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "src/variabili.scss";
.container-main {
  height: calc(100vh - 74px);
  background-color: $bg-primary;
  display: flex;
  align-items: center;
  .container-card {
    display: flex;
    flex-wrap: wrap;
    gap: 15px 30px;
    width: 70%;
    margin: auto;
  }
}
</style>
