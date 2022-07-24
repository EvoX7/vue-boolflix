<template>
  <div>
    <div class="container">
      <div id="hero" class="row m-auto mb-5 d-flex">
        <h1 class="mb-5 mt-5 text-white fw-bold">
          Unlimited movies, TV shows,<br />
          and more.
        </h1>

        <div class="input-group mb-3 w-50 m-auto entermail mb-5">
          <input
            type="text"
            class="form-control"
            placeholder="Email address"
            aria-label="Email address"
            aria-describedby="button-addon2"
          />
          <button
            class="btn btn-danger w-25 fw-bold fs-5"
            type="button"
            id="button-addon2"
          >
            Get Started <i class="fa-solid fa-chevron-right"></i>
          </button>
        </div>
      </div>
      <div class="row">
        <MoviesCard
          class="col-2 mb-3 mx-3"
          v-for="movie in movies"
          :key="movie.id"
          :movies="movie"
        />
        <SeriesCard
          class="col-2 mb-3 mx-3"
          v-for="tvShow in series"
          :key="tvShow.id"
          :series="tvShow"
        />

        <PopularMovies
          class="col-2 mb-3 mx-3"
          v-for="popular in populars"
          :key="popular.id"
          :populars="popular"
        />
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
  border-radius: 0px 0px 10px 10px;
}

#hero:before {
  content: "";
  position: absolute;
  z-index: -1;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background: url(../assets/Awesome-library.jpg);
  background-repeat: no-repeat;
  background-size: cover;
  opacity: 0.5;
  border-radius: 0px 0px 5px 5px;
}
</style>