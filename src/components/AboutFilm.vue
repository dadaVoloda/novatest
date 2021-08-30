<template>
  <div class="about-film">
    <movie-description></movie-description>
    <movie-reviews></movie-reviews>
    <movie-video></movie-video>
    <slider></slider>
  </div>
</template>

<script>
import MovieDescription from './MovieDescription.vue';
import MovieReviews from './MovieReviews.vue';
import MovieVideo from './MovieVideo.vue';
import Slider from './Slider.vue';
export default {
  components: { MovieDescription, MovieReviews, MovieVideo, Slider },
};
</script>

<style scoped lang="scss"></style>
