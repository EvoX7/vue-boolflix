<template>
  <header>
    <SearchBar @search="doSearch" />
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
</style>