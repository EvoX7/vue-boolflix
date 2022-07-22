<template>
  <div class="container">
    <div class="row m-auto">
      <h1 class="mb-5 mt-5 text-white fw-bold">
        Unlimited movies, TV shows,<br> 
        and more.
      </h1>

      <div class="input-group mb-3 w-50 m-auto entermail mb-5">
  <input type="text" class="form-control" placeholder="Email address" aria-label="Email address" aria-describedby="button-addon2">
  <button class="btn btn-danger w-25 fw-bold fs-5" type="button" id="button-addon2">Get Started <i class="fa-solid fa-chevron-right"></i></button>
</div>
      </div>
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

<style lang="scss" scoped>
h1 {
  padding-top: 100px;
  font-size: 70px;
}

.entermail {
  height: 60px;
}
</style>