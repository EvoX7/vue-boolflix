<template>
  <div>
  <!-- Tv series  -->
  <div class="card m-2 text-center">
    <div class="card-body d-flex flex-column">
      <img v-if="series.poster_path == null" src="../assets/notfound.png" />
      <img v-else :src="`${posterUrl}` + series.poster_path" />

      <div class="info">
        <h5 class="card-title fw-bold">{{ series.name }}</h5>
        <span>Original Title:</span>
        <h6 class="card-title fw-bold">{{ series.original_name }}</h6>
        <span>Original Language:</span>
        <span class="fw-bold">
          <img class="flags mx-2" v-if="series.original_language == 'en'" src="https://www.sic-info.org/wp-content/uploads/2014/01/us.png" />
          <img class="flags mx-2" v-else :src="`https://www.sic-info.org/wp-content/uploads/2014/01/${series.original_language}.png`" />
        </span>
        <span class="mx-2">Average vote:</span>
        <span><i v-for="star in avgVote(series.vote_average)" :key="star" class="fa-solid fa-star"></i></span>
        <p id="text" class="fw-bold">
          <span class="fs-6">Overview:</span>
          {{ series.overview }}
        </p>
      </div>
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: "SeriesCard",
  props: ["series"],

  data() {
    return {
      posterUrl: "https://image.tmdb.org/t/p/w342/",
    };
  },

  methods: {
    avgVote: function (userVote) {
      return Math.round(userVote / 2);
    },
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

.info {
  height: 36vh;
  position: relative;
  visibility: hidden;
}

.card {
  width: 26vh;
  height: 40vh;
  background-color: #cad1da;
  color: white;
  transition: 0.2s;
}

.card:hover {
  cursor: pointer;
  background-color: rgb(24, 24, 24);
}

.card:hover .info {
  bottom: 34vh;
  opacity: 1;
  visibility: visible;
  background-color: rgb(24, 24, 24);
}

#text {
  text-align: left;
  font-size: 13px;
  display: -webkit-box;
  -webkit-line-clamp: 9;
  -webkit-box-orient: vertical;
  overflow: hidden;
  text-overflow: ellipsis;
}

.fa-star {
  color: #c83749;
}
</style>