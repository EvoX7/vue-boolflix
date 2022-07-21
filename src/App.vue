<template>
  <div id="app">
    <!-- App vue is listening for Header $emit  -->
    <Header @search="movieSearch" @searching="seriesSearch" />

    <!-- Search information returns with props to MoviesList -->
    <MovieList :movies="movies" :series="series" />
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
      series: [],
    };
  },

  methods: {
    movieSearch: function (queryM) {
      axios
        .get(
          "https://api.themoviedb.org/3/search/movie?api_key=695f1e2cdece6cafb341504fdfa86fd0&language=it-IT&query=" +
            queryM
        )
        .then((response) => {
          this.movies = response.data.results;

          // Function reassigned and then returned with props to MoviesList
          this.searchInput = queryM;
          console.log(this.movies);
        });
    },

    seriesSearch: function (queryS) {
      axios
        .get(
          "https://api.themoviedb.org/3/search/tv?api_key=695f1e2cdece6cafb341504fdfa86fd0&language=it-IT&query=" +
            queryS
        )
        .then((response) => {
          this.series = response.data.results;

          // Function reassigned and then returned with props to MoviesList
          this.searchInput = queryS;
          console.log(this.series);
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