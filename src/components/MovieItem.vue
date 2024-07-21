<template>
  <div class="bg-teal-700 h-full border border-slate-300 p-1 cursor-pointer hover:-translate-y-2 hover:shadow-xl">
    <img class="w-full h-3/5" :src="movie.image" :alt="movie.title" >
    <h2 class="text-2xl p-1.5 text-white italic">{{ movie.title }}</h2>
    <p class="h-1/5 text-sm p-1.5">{{ movie.description }}</p>
    <p class="mb-2 text-xs p-1.5 text-white">{{ movie.tag }}</p>
    <button class="bg-teal-500 hover:bg-black hover:text-white border-2 border-white rounded-full p-1.5 mb-0" @click="toggleWishlist">{{ wishlistText }}</button>
  </div>
</template>

<script>
export default {
  props: {
    movie: Object,
    wishlist: Array
  },
  computed: {
    wishlistText() {
      return this.isInWishlist ? 'Verwijderen van wenslijst' : 'Toevoegen aan wenslijst';
    },
    isInWishlist() {
      return this.wishlist.some(item => item.id === this.movie.id);
    }
  },
  methods: {
    toggleWishlist() {
      this.$emit('toggleWishlist', this.movie);
    }
  }
};
</script>

