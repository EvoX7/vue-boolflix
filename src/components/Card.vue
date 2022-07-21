<template>
  <div class="card">
      <img :src="search.backdrop_path" class="card-img-top p-3" alt="poster" />
      <div class="card-body">
        <h4 class="card-title text-white fw-bold">{{search.title}}</h4>
        <h5 class="card-title text-white fw-bold">{{search.original_title}}</h5>
        <p class="card-text fw-bold">{{search.original_title}}</p>
        <p class="card-text">{{search.year}}</p>
      </div>
      <div class="card-body">
        <a href="#" class="card-link"></a>
      </div>
    </div>
</template>

<script>
export default {
  name: "Card",
  props: ["search"],
};
</script>

<style lang="scss">

li {
    list-style: none;
}
</style>