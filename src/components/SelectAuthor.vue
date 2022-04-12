<template>
  <select
    name="artist-option"
    v-model="artistaSelezionato"
    @change="$emit('ricercaArtista', artistaSelezionato)"
  >
    <option value="All">All</option>
    <option v-for="(artista, index) in artist" :key="index" :value="artista">
      {{ artista }}
    </option>
  </select>
</template>

<script>
export default {
  name: "SelectAuthor",
  data() {
    return {
      artistaSelezionato: "All",
    };
  },
  props: {
    artist: Array,
  },
};
</script>

<style lang="scss" scoped>
@import "src/variabili.scss";
select {
  border: 1px solid $bg-secondary;
  background-color: $bg-secondary;
  color: white;
  border-radius: 10px;
  padding: 5px;
}
</style>
