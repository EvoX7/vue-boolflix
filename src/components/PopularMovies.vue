<template>
  <div>
    <!-- Popular Movies  -->
    <div class="card m-2 text-center">
      <div class="card-body d-flex flex-column">
        <img v-if="populars.poster_path == null" src="../assets/notfound.png" />
        <img v-else :src="`${posterUrl}` + populars.poster_path" />

        <div class="info">
          <h5 class="card-title fw-bold">{{ populars.title }}</h5>
          <span>Original Title:</span>
          <h6 class="card-title fw-bold">{{ populars.original_title }}</h6>
          <span>Original Language:</span>
          <span class="fw-bold">
            <img
              class="flags mx-2"
              v-if="populars.original_language == 'en'"
              src="https://www.sic-info.org/wp-content/uploads/2014/01/us.png"
            />
            <img
              class="flags mx-2"
              v-else
              :src="`https://www.sic-info.org/wp-content/uploads/2014/01/${populars.original_language}.png`"
            />
          </span>
          <span class="mx-2">Average vote:</span>
          <span
            ><i
              v-for="star in avgVote(populars.vote_average)"
              :key="star"
              class="fa-solid fa-star"
            ></i
          ></span>
          <br>
          <p id="text" class="fw-bold">
            <span class="fs-6">Overview:</span>
            {{ populars.overview }}
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "PopularMovies",
  props: ["populars"],

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
  /* Remove the height property to allow the content to determine the height */
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  padding: 10px;
  background-color: rgb(24, 24, 24);
  color: white;
  visibility: hidden;
  opacity: 0;
  transition: visibility 0s, opacity 0.3s;
}

.card {
  /* Set a maximum height for the card */
  max-height: 400px;
  background-color: #cad1da;
  color: white;
  position: relative;
  overflow: hidden; /* Add overflow: hidden to prevent text overflow */
}

.card-title {
  /* Add ellipsis to long titles */
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

.card-body {
  /* Set the card body to occupy remaining space */
  flex: 1;
  display: flex;
  flex-direction: column;
}

.card:hover {
  cursor: pointer;
  background-color: rgb(24, 24, 24);
}

.card:hover .info {
  visibility: visible;
  opacity: 1;
}

#text {
  /* Limit text to 3 lines with ellipsis */
  font-size: 10px;
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
  text-overflow: ellipsis;
}


.fa-star {
  color: #c83749;
}
</style>
