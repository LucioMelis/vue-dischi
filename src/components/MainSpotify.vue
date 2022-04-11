<template>
  <div class="container-main">
    <!-- Sezione Option -->
    <div class="select-disc">
      <h4>Seleziona il genere:</h4>
      <select name="disc-option">
        <option value="all">All</option>
        <option value="pop">Pop</option>
        <option value="metal">Metal</option>
        <option value="rock">Rock</option>
        <option value="jazz">Jazz</option>
      </select>
    </div>
    <!-- Sezione Dischi  -->
    <div v-if="disc.length > 0" class="container-card">
      <CardDisc v-for="(song, index) in disc" :key="index" :songdisc="song" />
    </div>
    <!-- Sezione Caricamento  -->
    <div class="spinner" v-else>
      <Loading />
    </div>
  </div>
</template>

<script>
import CardDisc from "../components/CardDisc.vue";
import axios from "axios";
import Loading from "../components/Loading.vue";

export default {
  name: "MainSpotify",
  components: {
    CardDisc,
    Loading,
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
        console.log(this.disc);
        // console.log(this.disc[0]);
      });
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "src/variabili.scss";
.container-main {
  min-height: calc(100vh - 74px);
  background-color: $bg-primary;
  .select-disc {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 10px 0;
    h4 {
      color: $text-color;
      padding-right: 10px;
    }
    select {
      border: 1px solid black;
      background-color: $bg-secondary;
      color: white;
      border-radius: 10px;
      padding: 5px;
    }
  }
  .container-card {
    display: flex;
    flex-wrap: wrap;
    gap: 15px 30px;
    width: 70%;
    margin: auto;
    padding: 10px 0;
  }
  .spinner {
    display: flex;
    justify-content: center;
    padding-top: 200px;
  }
}
</style>
