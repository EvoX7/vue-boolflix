<template>
  <header>
    <nav class="navbar navbar-expand-lg navbar-light">
      <div class="container-fluid">
        <a href=".">
          <img class="ms-3" id="logo" src="../assets/Awesome.png" alt="logo"
        /></a>
        <button
          class="navbar-toggler"
          type="button"
          data-bs-toggle="collapse"
          data-bs-target="#navbarSupportedContent"
          aria-controls="navbarSupportedContent"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="ms-4 collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="navbar-nav me-auto mb-2 mb-lg-0">
            <li class="nav-item">
              <a class="nav-link fw-bold" aria-current="page" href="#">Home</a>
            </li>
            <li class="nav-item">
              <a class="nav-link fw-bold" href="#">Tv Series</a>
            </li>
            <li class="nav-item">
              <a class="nav-link fw-bold" href="#">Movies</a>
            </li>
            <li class="nav-item">
              <a class="nav-link fw-bold" href="#">Originals</a>
            </li>
            <li class="nav-item">
              <a class="nav-link fw-bold" href="#">New on Awesomeflix</a>
            </li>
            <li class="nav-item">
              <a class="nav-link fw-bold" href="#">My List</a>
            </li>
          </ul>
          <SearchBar class="me-5" @search="doSearch" />
        </div>
      </div>
    </nav>
  </header>
</template>

<script>
import SearchBar from "./SearchBar.vue";

export default {
  name: "Header",
  components: {
    SearchBar,
  },

  methods: {
    doSearch: function (searchText) {
      this.$emit("search", searchText);
    },
  },
};
</script>

<style lang="scss">
nav {
  background-color: #dee0e6;
}

#logo {
  width: 180px;
  height: 55px;
}
</style>