<template>
  <div class="container">
    <div class="row m-auto">
      <h1 class="mb-5 mt-5 fw-bold">Your selected movies</h1>
      <div class="col-12 d-flex flex-wrap mt-3">
        <MoviesCard
          class="col-2 mb-3 mx-3 card"
          v-for="movie in movies"
          :key="movie.id"
          :movies="movie"
        />
        <SeriesCard
          class="col-2 mb-3 mx-3 card"
          v-for="tvShow in series"
          :key="tvShow.id"
          :series="tvShow"
        />
      </div>
      
    </div>
  </div>
</template>

<script>
import MoviesCard from "./MoviesCard.vue";
import SeriesCard from "./SeriesCard.vue";

export default {
  name: "DisplayList",

  components: {
    MoviesCard,
    SeriesCard,
  },

  props: ["movies", "series"],
};


</script>

<style lang="scss">
</style>