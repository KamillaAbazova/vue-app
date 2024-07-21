<template>
  <div class="flex justify-around px-4">
  <div>
    <h1 class="text-3xl font-bold text-white mb-10 mt-6 tracking-widest bg-teal-500 uppercase">Mijn films</h1>
    <div :class="wishlist.length > 0 ? 'md:w-3/4 w-full' : 'w-full'">
      <MovieGrid :movies="movies" :wishlist="wishlist" @toggleWishlist="toggleWishlist" />
    </div>
  </div>
    <WishList v-if="wishlist.length > 0" :wishlist="wishlist" @remove="toggleWishlist" />
  </div>
</template>

<script>
import MovieGrid from './components/MovieGrid.vue';
import WishList from './components/WishList.vue';
import movies from './assets/movies.json';

export default {
  components: {
    MovieGrid,
    WishList
  },
  data() {
    return {
      movies,
      wishlist: []
    };
  },
  methods: {
    toggleWishlist(movie) {
      const index = this.wishlist.findIndex(item => item.id === movie.id);
      if (index === -1) {
        this.wishlist.push(movie);
      } else {
        this.wishlist.splice(index, 1);
      }
      this.saveWishlist();
    },
    saveWishlist() {
      document.cookie = `wishlist=${JSON.stringify(this.wishlist)}; path=/`;
    },
    loadWishlist() {
      const cookie = document.cookie.split('; ').find(row => row.startsWith('wishlist='));
      if (cookie) {
        this.wishlist = JSON.parse(cookie.split('=')[1]);
      }
    }
  },
  created() {
    this.loadWishlist();
  }
};
</script>

