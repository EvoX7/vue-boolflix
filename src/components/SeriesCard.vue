<template>
  <div>

     <!-- Tv series  -->
    <div class="card h-100" >
      <div class="card-body d-flex flex-column">
        <h4 class="card-title fw-bold">{{ series.name }}</h4>
        <span>Original Title:</span>
        <h6 class="card-title fw-bold">{{ series.original_name }}</h6>
        <span>Original Language:</span>
        <p class="card-text fw-bold"><img v-if="series.original_language == 'en'" src="https://www.sic-info.org/wp-content/uploads/2014/01/us.png" width="16px" height="11px">
        <img v-else if :src="`https://www.sic-info.org/wp-content/uploads/2014/01/${series.original_language}.png`" width="16px" height="11px">
         <span> </span></p>
        <span>Average vote:</span>
        <p class="card-text">{{ series.vote_average }}</p>
        
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SeriesCard",
  props: ["series"],
};
</script>

<style lang="scss">
li {
  list-style: none;
}
</style>