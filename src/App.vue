<template>
  <div id="app">
    <!-- App vue is listening for Header $emit  -->
    <Header @search="makeSearch" />

    <!-- Informations returns with props to DisplayList -->
    <DisplayList :movies="movies" :series="series" :populars="populars" />
  </div>
</template>

<script>
import axios from "axios";
import Header from "./components/Header.vue";
import DisplayList from "./components/DisplayList.vue";

export default {
  name: "App",
  components: {
    Header,
    DisplayList,
  },

  data: function () {
    return {
      movies: [],
      series: [],
      populars: [],
      searchInput: "",
    };
  },

  methods: {
    movieSearch: function (queryM) {
      axios
        .get(
          "https://api.themoviedb.org/3/search/movie?api_key=695f1e2cdece6cafb341504fdfa86fd0&language=en-EN&query=" +
            queryM
        )
        .then((response) => {
          this.movies = response.data.results;
          console.log(this.movies);
        })
        .catch((error) => {
          console.log(error);
        });
    },

    seriesSearch: function (queryS) {
      axios
        .get(
          "https://api.themoviedb.org/3/search/tv?api_key=695f1e2cdece6cafb341504fdfa86fd0&language=en-EN&query=" +
            queryS
        )
        .then((response) => {
          this.series = response.data.results;
          console.log(this.series);
        })
        .catch((error) => {
          console.log(error);
        });
    },

    makeSearch: function (query) {
      this.movieSearch(query);
      this.seriesSearch(query);
    },

    // Display popular movies Homepage
    displayPopular: function () {
      axios
        .get(
          "https://api.themoviedb.org/3/movie/popular?api_key=695f1e2cdece6cafb341504fdfa86fd0&language=en-EN&page=1"
        )
        .then((response) => {
          this.populars = response.data.results;
          console.log(this.populars);
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
  mounted() {
      this.displayPopular();
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

body {
  background-color: #134e6f;
  opacity: 0.9;
}
</style>