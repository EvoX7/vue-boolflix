<template>
  <div class="row p-5">
    <div class="col-10 m-auto">
      <h1 class="mb-5 fw-bold">Your selected movies</h1>
      <Card />
    </div>
  </div>
</template>

<script>
import Card from "./Card.vue";
export default {
  name: "MovieList",
  components: {
    Card,
  }
};
</script>

<style>
</style>