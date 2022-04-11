<template>
  <div class="container-main">
    <!-- Sezione Option -->
    <div class="select-disc">
      <h4>Seleziona il genere:</h4>
      <select
        name="disc-option"
        v-model="genereSelezionato"
        @change="cambioGenere()"
      >
        <option value="All">All</option>
        <option value="Pop">Pop</option>
        <option value="Metal">Metal</option>
        <option value="Rock">Rock</option>
        <option value="Jazz">Jazz</option>
      </select>
    </div>
    <!-- Sezione Dischi  -->
    <div v-if="disc.length > 0" class="container-card">
      <CardDisc
        v-for="(song, index) in cambioGenere()"
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

export default {
  name: "MainSpotify",
  components: {
    CardDisc,
    Loading,
  },
  data() {
    return {
      disc: [],
      genereSelezionato: "All",
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
    cambioGenere() {
      console.log(this.genereSelezionato);
      if (this.genereSelezionato === "All") {
        return this.disc;
      }
      return this.disc.filter((item) =>
        item.genre.includes(this.genereSelezionato)
      );
      // inserire il filtro dell'array in base al genere selezinato
      // una volta che funziona questo faccio un commit e procedo a fare
      // il componente con l $emit
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
    select {
      border: 1px solid $bg-secondary;
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
