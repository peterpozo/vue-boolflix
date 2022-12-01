<template>
  <div>
    <ul v-for="objMovie in arrMovies" :key="objMovie.id">
      <li>{{ objMovie.title }}</li>
      <li>{{ objMovie.original_language }}</li>
      <li>{{ objMovie.vote_average }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "MainPage",
  props: {
    arrMovies: Array,
  },
};
</script>

<style lang="scss" scoped></style>
