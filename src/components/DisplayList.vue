<template>
  <div>
  <div id="hero" class="row m-auto mb-5">
    <h1 class="mb-5 mt-5 text-white fw-bold">
      Unlimited movies, TV shows,<br>
      and more.
    </h1>

    <div class="input-group mb-3 w-25 m-auto entermail mb-5">
      <input type="email" class="form-control" placeholder="Email address" aria-label="Email address" aria-describedby="button-addon2" />
      <button class="btn btn-danger fw-bold fs-5" type="button" id="button-addon2">
        Get Started <i class="fa-solid fa-chevron-right"></i>
      </button>
    </div>
  </div>

  <div class="container">
    <div class="row">
      <PopularMovies class="col-2 mb-3 mx-5" v-for="popular in populars" :key="popular.id" :populars="popular" />
      <MoviesCard class="col-2 mb-3 mx-5" v-for="movie in movies" :key="movie.id" :movies="movie" />
      <SeriesCard class="col-2 mb-3 mx-5" v-for="tvShow in series" :key="tvShow.id" :series="tvShow" />
      
    </div>
  </div>
</div>
</template>

<script>
import MoviesCard from "./MoviesCard.vue";
import SeriesCard from "./SeriesCard.vue";
import PopularMovies from "./PopularMovies.vue";

export default {
  name: "DisplayList",

 data() {
    return {
      displayTitle: "movies",
      
    };
  },

  components: {
    MoviesCard,
    SeriesCard,
    PopularMovies,
  },

  props: ["movies", "series", "populars"],

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

#hero {
  position: relative;
  z-index: 1;
  background-color: black;
  border-bottom: 5px solid #cad1da;
}

#hero:before {
  content: "";
  position: absolute;
  z-index: -1;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background: url(../assets/Awesome-library.png);
  background-repeat: no-repeat;
  background-size: cover;
  opacity: 0.5;
}
</style>