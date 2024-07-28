<template>
  <div class="flex ml-6 cursor-pointer">
    <img
      v-for="star in 5"
      :key="star"
      @click="setRating(star)"
      :src="star <= value ? 'https://img.icons8.com/?size=32&id=zX00FT5x6S7M&format=png' : 'https://img.icons8.com/?size=32&id=16101&format=png'"
      class="h-6 w-6"
      alt="star"
    />
  </div>
</template>

<script>
export default {
  props: {
    value: {
      type: Number,
      default: 0
    }
  },
  methods: {
    setRating(star) {
      this.$emit('changeRating', star);
    }
  }
};
</script>