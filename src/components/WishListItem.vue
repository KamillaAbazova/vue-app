<template>
  <div class="w-96">
    <ul>
    <li class="mb-4 text-xl text-white">
    {{ movie.title }} - <span class="text-base">{{ movie.tag }}</span>
    <button class="text-red-600 ml-6" @click="removeFromWishlist">X</button>
    </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    movie: Object
  },
  methods: {
    removeFromWishlist() {
      this.$emit('remove', this.movie);
    }
  }
};
</script>

