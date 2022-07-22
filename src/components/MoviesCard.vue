<template>
  <div>
    <!-- Movies  -->
    <div class="card h-100">
      <div class="card-body d-flex flex-column">
        <img v-if="movies.poster_path == null" src="../assets/notfound.png" />
        <img v-else :src="`${posterUrl}` + movies.poster_path" />
        <h4 class="card-title fw-bold">{{ movies.title }}</h4>
        <span>Original Title:</span>
        <h6 class="card-title fw-bold">{{ movies.original_title }}</h6>
        <span>Original Language:</span>
        <p class="card-text fw-bold">
          <img
            class="flags"
            v-if="movies.original_language == 'en'"
            src="https://www.sic-info.org/wp-content/uploads/2014/01/us.png"
          />
          <img
            class="flags"
            v-else
            if
            :src="`https://www.sic-info.org/wp-content/uploads/2014/01/${movies.original_language}.png`"
          />
          <span> </span>
        </p>
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

  data() {
    return {
      posterUrl: "https://image.tmdb.org/t/p/w342/",
    };
  },
};
</script>

<style lang="scss" scoped>
li {
  list-style: none;
}

.flags {
  width: 18px;
  height: 12px;
}
</style>