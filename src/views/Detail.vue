<template>
  <div class="movie-detail">
    <MovieCard :movie="movie" />
  </div>
</template>

<script>
import { useRoute } from "vue-router";
// import env from "@/env.js";
import movies from "./movies.json";
import MovieCard from "../components/MovieCard.vue";

export default {
  data() {
    return {
      movie: {},
      movieId: "",
    };
  },
  components: {
    MovieCard,
  },

  mounted() {
    const route = useRoute();
    const id = route.params.id;
    this.movie = movies.filter((movie) => movie.id === id)[0];
  },

  computed: {
    getDataFilter() {
      return this.movies1.filter(
        (item) =>
          item.title
            .toLocaleLowerCase()
            .indexOf(this.searchMovies.toLocaleLowerCase()) > -1
      );
    },
  },
};
</script>

<style lang="scss"></style>
