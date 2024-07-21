<template>
 <div :class="wishlist.length > 0 ? 'grid grid-cols-3 gap-6' : 'grid grid-cols-4 gap-6'">
    <MovieItem v-for="movie in movies" :key="movie.id" :movie="movie" :wishlist="wishlist" @toggleWishlist="toggleWishlist" />
  </div>
</template>

<script>
import MovieItem from './MovieItem.vue';

export default {
  props: {
    movies: Array,
    wishlist: Array
  },
  components: {
    MovieItem
  },
  methods: {
    toggleWishlist(movie) {
      this.$emit('toggleWishlist', movie);
    }
  }
};
</script>


