<template>
  <select
    name="disc-option"
    v-model="genereSelezionato"
    @change="$emit('ricerca', genereSelezionato)"
  >
    <option value="All">All</option>
    <option value="Pop">Pop</option>
    <option value="Metal">Metal</option>
    <option value="Rock">Rock</option>
    <option value="Jazz">Jazz</option>
  </select>
</template>

<script>
export default {
  name: "SelectSearch",
  data() {
    return {
      genereSelezionato: "All",
    };
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

