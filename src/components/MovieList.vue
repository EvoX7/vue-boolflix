<template>
  <div class="row p-5">
    <h1 class="mb-5 fw-bold">Your selected movies</h1>
    <div class="col-10 m-auto d-flex flex-wrap mt-3">
      <Card class="col-2 mb-4" v-for="movie in movies" :key="movie" :movies="movie" />
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

<style>
</style>