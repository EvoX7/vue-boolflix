<template>
  <div class="container">
    <div class="row m-auto">
      <h1 class="mb-5 mt-5 fw-bold">Your selected movies</h1>
      <div class="col-12 d-flex flex-wrap mt-3">
        <Card
          class="col-2 mb-3 mx-3 card"
          v-for="movie in movies"
          :key="movie"
          :movies="movie"
        />
      </div>
    </div>
  </div>
</template>

<script>
import Card from "./Card.vue";
export default {
  name: "MovieList",

  components: {
    Card,
  },

  props: ["movies"],
};
</script>

<style lang="scss">
</style>