<template>
  <div class="container-main">
    <!-- Sezione Option -->
    <div class="select-disc">
      <h4>Seleziona il genere:</h4>
      <SelectSearch @ricerca="filtroGenere" />
    </div>
    <!-- Sezione Dischi  -->
    <div v-if="disc.length > 0" class="container-card">
      <CardDisc
        v-for="(song, index) in cambioGenere"
        :key="index"
        :songdisc="song"
      />
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
import SelectSearch from "../components/SelectSearch.vue";

export default {
  name: "MainSpotify",
  components: {
    CardDisc,
    Loading,
    SelectSearch,
  },
  data() {
    return {
      disc: [],
      genere: "",
    };
  },
  mounted() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((response) => {
        this.disc = response.data.response;
        // console.log(this.disc);
        // console.log(this.disc[0]);
      });
  },
  methods: {
    filtroGenere(genereSelezionato) {
      // console.log(genereSelezionato);
      this.genere = genereSelezionato;
    },
  },
  computed: {
    cambioGenere() {
      if (this.genere === "All") {
        return this.disc;
      }
      return this.disc.filter((item) => item.genre.includes(this.genere));
    },
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
