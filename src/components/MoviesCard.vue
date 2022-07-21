<template>
  <div>

    <!-- Movies  -->
    <div class="card">
      <div class="card-body d-flex flex-column">
        <h4 class="card-title fw-bold">{{ movies.title }}</h4>
        <span>Original Title:</span>
        <h6 class="card-title fw-bold">{{ movies.original_title }}</h6>
        <span>Original Language:</span>
        <p class="card-text fw-bold">{{ movies.original_language }}</p>
        <span>Average vote:</span>
        <p class="card-text">{{ movies.vote_average }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MoviesCard",
  props: ["movies"],
};
</script>

<style lang="scss">
li {
  list-style: none;
}
</style>