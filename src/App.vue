<template>
  <div id="app">
    <!-- App vue is listening for Header emit  -->
    <Header @search="movieSearch" />

    <!-- Search information returns with props to MoviesList -->
    <MovieList :movies="movies" />
  </div>
</template>

<script>
import axios from "axios";
import Header from "./components/Header.vue";
import MovieList from "./components/MovieList.vue";

export default {
  name: "App",
  components: {
    Header,
    MovieList,
  },

  data: function () {
    return {
      movies: [],
    };
  },

  methods: {
    movieSearch: function (query) {
      axios
        .get(
          "https://api.themoviedb.org/3/search/movie?api_key=695f1e2cdece6cafb341504fdfa86fd0&language=it-IT&query=" +
            query
        )
        .then((response) => {
          this.movies = response.data.results;

          // Function reassigned and then returned with props to MoviesList
          this.searchInput = query;
          console.log(this.movies);
        });
    },

     created() {
    this.movieSearch();
  },
  },
};
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap.scss";

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>