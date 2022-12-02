<template>
  <main class="container">
    <section class="movies">
      <div
        class="row row-cols-1 row-cols-sm-2 row-cols-md-3 row-cols-lg-4 row-cols-xl-3 g-5"
      >
        <PageCard
          v-for="objMovie in arrMovies"
          :key="objMovie.id"
          :title="objMovie.title"
          :originalTitle="objMovie.original_title"
          :language="objMovie.original_language"
          :score="objMovie.vote_average"
          :imgUrl="'https://image.tmdb.org/t/p/w342' + objMovie.poster_path"
        />
      </div>
    </section>
    <section class="tv">
      <div
        class="row row-cols-1 row-cols-sm-2 row-cols-md-3 row-cols-lg-4 row-cols-xl-3 g-5"
      >
        <PageCard
          v-for="objTv in arrTv"
          :key="objTv.id"
          :title="objTv.name"
          :originalTitle="objTv.original_name"
          :language="objTv.original_language"
          :score="objTv.vote_average"
          :imgUrl="'https://image.tmdb.org/t/p/w342' + objTv.poster_path"
        />
      </div>
    </section>
  </main>
</template>

<script>
import PageCard from "@/components/PageCard.vue";
export default {
  name: "MainPage",
  components: {
    PageCard,
  },
  props: {
    arrMovies: Array,
    arrTv: Array,
  },
};
</script>

<style lang="scss" scoped>
@import "~bootstrap/scss/bootstrap";

.movies {
  margin-top: 10rem;
}
</style>
