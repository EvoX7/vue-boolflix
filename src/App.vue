<template>
  <div id="app">
    <!-- App vue is listening for Header $emit  -->
    <Header @search="makeSearch" />

    <!-- Search information returns with props to DisplayList -->
    <DisplayList :movies="movies" :series="series" />
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
          console.log(this.movies);
        })
        .catch((error) => {
          console.log(error);
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
}
</style>