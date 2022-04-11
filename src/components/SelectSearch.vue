<template>
  <div class="select-disc">
    <h4>Seleziona il genere:</h4>
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
  </div>
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
</style>

