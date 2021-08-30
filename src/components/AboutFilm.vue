<template>
  <div class="about-film">
    <movie-description></movie-description>
    <movie-reviews></movie-reviews>
  </div>
</template>

<script>
import MovieDescription from './MovieDescription.vue';
import MovieReviews from './MovieReviews.vue';
export default {
  components: { MovieDescription, MovieReviews },
};
</script>

<style scoped lang="scss"></style>
