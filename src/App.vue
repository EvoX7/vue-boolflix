<template>
  <div id="app">
    <Header />
    <Main />
    <MoviesList />
    <Card />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";
import MovieList from "./components/MovieList.vue";
import Card from "./components/Card.vue";

export default {
  name: "App",
  components: {
    Header,
    Main,
    MovieList,
    Card,
  },

  data: function () {
    return {
      movies: [],
    };
  },

  methods: {
    movieSearch: function () {
      axios.get("https://api.themoviedb.org/3/search/movie?api_key=695f1e2cdece6cafb341504fdfa86fd0")
        .then((response) => {
        this.movies = response.data.results;
        console.log(this.movies)
      });
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