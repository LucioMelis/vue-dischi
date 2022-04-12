<template>
  <div class="container-main">
    <!-- Sezione Option -->
    <div class="select-disc">
      <h4>Seleziona il genere:</h4>
      <!-- Sezione Select Genere  -->
      <SelectSearch @ricerca="filtroGenere" />
      <!-- Sezione Select Artista  -->
      <h4>Seleziona Artista:</h4>
      <SelectAuthor :artist="arrayArtisti" @ricercaArtista="filtroArtista" />
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
import SelectAuthor from "../components/SelectAuthor.vue";

export default {
  name: "MainSpotify",
  components: {
    CardDisc,
    Loading,
    SelectSearch,
    SelectAuthor,
  },
  data() {
    return {
      disc: [],
      arrayArtisti: [],
      genere: "",
      author: "",
    };
  },
  mounted() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((response) => {
        this.disc = response.data.response;
        this.disc.filter((item) => this.arrayArtisti.push(item.author));
        // console.log(this.arrayArtisti);
        // console.log(this.disc);
        // console.log(this.disc[0]);
      });
  },
  methods: {
    filtroGenere(genereSelezionato) {
      // console.log(genereSelezionato);
      this.genere = genereSelezionato;
    },
    filtroArtista(artistaSelezionato) {
      console.log(artistaSelezionato);
      this.author = artistaSelezionato;
    },
  },

  computed: {
    cambioGenere() {
      if (this.genere === "All") {
        return this.disc;
      }
      return this.disc.filter((item) => {
        return item.genre.includes(this.genere);
      });
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
