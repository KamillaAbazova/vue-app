<template>
  <div class="bg-teal-950 w-full ml-0 p-4">
    <h2 class="mt-4 mb-8 text-4xl text-white italic">Wenslijst</h2>
    <ul>
      <WishListItem v-for="movie in wishlist" :key="movie.id" :movie="movie" @remove="removeFromWishlist" />
    </ul>
  </div>
</template>

<script>
import WishListItem from './WishListItem';

export default {
  props: {
    wishlist: Array
  },
  components: {
  WishListItem
  },
  methods: {
    removeFromWishlist(movie) {
      this.$emit('remove', movie);
    }
  }
};
</script>

