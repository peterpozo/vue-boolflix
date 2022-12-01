<template>
  <div>
    <HeaderPage @queryChange="search" />
    <MainPage :arrMovies="arrMovies" />
  </div>
</template>

<script>
import axios from "axios";
import HeaderPage from "@/components/HeaderPage.vue";
import MainPage from "@/components/MainPage.vue";
export default {
  name: "App",
  components: {
    HeaderPage,
    MainPage,
  },
  data() {
    return {
      baseApiUrl: "https://api.themoviedb.org/3",
      apiKey: "c55e3f8ac58ea6481cddd7c531b026ba",
      resultLanguage: "it-IT",
      arrMovies: [],
    };
  },
  methods: {
    search(queryString) {
      axios
        .get(this.baseApiUrl + "/search/movie", {
          params: {
            api_key: this.apiKey,
            query: queryString,
            language: this.resultLanguage,
          },
        })
        .then((responseAxios) => {
          this.arrMovies = responseAxios.data.results;
          console.log(this.arrMovies);
        });
    },
  },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Roboto:ital,wght@0,100;0,300;0,400;0,500;0,700;0,900;1,100;1,300;1,400;1,500;1,700;1,900&display=swap");

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Roboto", sans-serif;
}

html {
  color: #fff;
  background: black;
}
</style>
