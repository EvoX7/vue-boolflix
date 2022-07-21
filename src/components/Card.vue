<template>
  <div class="card">
      <div class="card-body">
        <h4 class="card-title text-white fw-bold">{{movies.title}}</h4>
        <h5 class="card-title text-white fw-bold">{{movies.original_title}}</h5>
        <p class="card-text fw-bold">{{movies.original_language}}</p>
        <p class="card-text">{{movies.vote_average}}</p>
      </div>
    </div>
</template>

<script>
export default {
  name: "Card",
  props: ["movies"],
};
</script>

<style lang="scss">

li {
    list-style: none;
}

.card {
   
}
</style>