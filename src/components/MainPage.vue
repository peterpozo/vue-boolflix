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
          :date="objMovie.release_date"
          :language="objMovie.original_language"
          :score="convertScore(objMovie.vote_average)"
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
          :date="objTv.release_date"
          :language="objTv.original_language"
          :score="convertScore(objTv.vote_average)"
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
  methods: {
    convertScore(score) {
      //score : 10 = voto_desiderato : 5;
      // voto_desiderato => score * 5 / 10 => *0.5 => score / 2
      const maxScore = 5;
      const originalMaxScore = 10;
      return {
        score: Math.ceil((score * maxScore) / originalMaxScore),
        maxScore: maxScore,
      };
    },
  },
};
</script>

<style lang="scss" scoped>
@import "~bootstrap/scss/bootstrap";

.movies {
  margin-top: 10rem;
}
</style>
