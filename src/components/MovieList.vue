<template>
  <div class="row p-5">
    <div class="col-10 m-auto">
      <h1 class="mb-5 fw-bold">Your selected movies</h1>
      <Card
      v-for="movie in movies"
          :key="movie"
          :search="search"
       />
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

  props: ["search"],
};
</script>

<style>
</style>