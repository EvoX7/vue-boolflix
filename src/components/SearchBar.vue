<template>
  <nav class="navbar navbar-expand-lg navbar-light">
    <div class="me-5 container d-flex justify-content-center">
      <div class="d-flex">
        <input
          class="form-control me-2"
          type="search"
          placeholder="Find movies or tv series"
          aria-label="Search"
          v-model="searchInput"
          @keyup.enter="$emit('search', searchInput)"
        />
        <button class="btn btn-danger fw-bold" @click="$emit('search', searchInput)">
          Search
        </button>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  data: function () {
    return {
      searchInput: "",
    };
  },
};
</script>

<style lang="scss" scoped>
</style>