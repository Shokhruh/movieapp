<template>
  <ul class="movie_list list-group">
    <MovieListItem
      v-for="movie in movies"
      v-bind:movie="movie"
      v-bind:class="[{ liked: movie.liked }, { favourited: movie.favourited }]"
      :key="movie.id"
      @onToggle="$emit('onToggle', $event)"
      @onDelete="$emit('onDelete', movie.id)"
    />
  </ul>
</template>

<script>
import MovieListItem from "@/components/movie-list-item/MovieListItem.vue";
export default {
  components: {
    MovieListItem,
  },
  props: {
    movies: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style></style>
