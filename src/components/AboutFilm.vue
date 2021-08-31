<template>
  <div class="about-film">
    <movie-description></movie-description>
    <movie-reviews></movie-reviews>
    <movie-video></movie-video>
    <slider @open="changePicture" :width="width"></slider>
  </div>
</template>

<script>
import MovieDescription from './MovieDescription.vue';
import MovieReviews from './MovieReviews.vue';
import MovieVideo from './MovieVideo.vue';
import Slider from './Slider.vue';
export default {
  components: { MovieDescription, MovieReviews, MovieVideo, Slider },
  props: {
    width: {
      type: Number,
    },
  },
  data() {
    return {
      picture: {},
    };
  },
  methods: {
    changePicture(item) {
      this.picture = item;
      this.$emit('openModal', this.picture.image);
    },
  },
};
</script>

<style scoped lang="scss"></style>
