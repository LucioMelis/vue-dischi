<template>
  <div class="content-card-disc">
    <img :src="songdisc.poster" :alt="songdisc.title" />
    <h2>{{ songdisc.title }}</h2>
    <p>{{ songdisc.author }}</p>
    <p>{{ songdisc.year }}</p>
  </div>
</template>

<script>
export default {
  name: "CardDisc",
  props: {
    songdisc: Object,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "src/variabili.scss";
.content-card-disc {
  width: calc(20% - 30px * 4 / 5);
  padding: 20px;
  background-color: $bg-secondary;
  text-align: center;
  h2 {
    color: white;
    padding: 15px 0;
  }
  p {
    color: $text-color;
    padding: 3px 0;
  }
  img {
    aspect-ratio: 1/1;
    width: 100%;
  }
}
</style>
