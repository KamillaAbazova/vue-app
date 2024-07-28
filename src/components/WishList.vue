<template>
  <div class="bg-teal-950 w-full ml-0 p-4">
    <h2 class="mt-4 mb-8 text-4xl text-white italic">Wenslijst</h2>
    <draggable :list="wishlist" tag="ul" @end="onEnd">
      <template #item="{ element: movie }">
        <WishListItem :movie="movie" @remove="removeFromWishlist(movie)" @update="watchedMovie" />
      </template>
    </draggable>
  </div>
</template>

<script>
import draggable from 'vuedraggable';
import WishListItem from './WishListItem';

export default {
  props: {
    wishlist: {
    type: Array,
    default: () => []
    }
  },
  components: {
  draggable,
  WishListItem
  },
  methods: {
    removeFromWishlist(movie) {
      this.$emit('remove', movie);
    },
    watchedMovie(updatedMovie) {
      const index = this.wishlist.findIndex(item => item.id === updatedMovie.id);
      if (index !== -1) {
        this.wishlist.splice(index, 1, updatedMovie);
        this.saveWishlist();
      }
    },
    onEnd() {
      this.$emit('update:wishlist', this.wishlist);
      this.saveWishlist();
    },
    saveWishlist() {
      document.cookie = `wishlist=${JSON.stringify(this.wishlist)}; path=/`;
    }
  }
};
</script>

