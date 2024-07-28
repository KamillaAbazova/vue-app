<template>
  <div class="w-96">
    <ul>
    <li :class="{ 'text-black': movie.isWatched, 'bg-teal-500': movie.isWatched }" class="mb-4 text-xl text-white">
    <input v-model="movie.isWatched" type="checkbox" @change="watchedMovie" class="mr-2"/>
    {{ movie.title }} - <span class="text-base">{{ movie.tag }}</span>
    <button class="text-red-600 ml-6" @click="removeFromWishlist">X</button>
    <Rating :value="movie.rating" @changeRating="onRatingChange" />
    </li>
    </ul>
  </div>
</template>

<script>
import Rating from "./Rating.vue";
export default {
  props: {
    movie: Object
  },
  components: {
    Rating
  },
  methods: {
    watchedMovie() {
      this.$emit('update', this.movie);
    },
    onRatingChange(newRating) {
    this.movie.rating = newRating;
      this.$emit('update', this.movie);
    },
    removeFromWishlist() {
      this.$emit('remove', this.movie);
    }
  }
};
</script>

