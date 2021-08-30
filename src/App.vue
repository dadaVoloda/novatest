<template>
  <div>
    <header class="header">
      <div class="header__container">
        <movie :movie="movie"></movie>
      </div>
    </header>
    <main></main>
    <footer></footer>
  </div>
</template>

<script>
import Movie from './components/Movie.vue';
export default {
  components: { Movie },
  data() {
    return {
      movie: {
        title: 'Deadpool',
        year: 2016,
        country: 'usa',
        premission: '18+',
      },
    };
  },
};
</script>

<style lang="scss">
#app {
  position: relative;
  min-height: 100vh;
  font-family: 'HelveticaNeueThin', sans-serif;
  font-size: 18px;
  color: $dark;
  background-color: $dark;
  background-image: url('./assets/img/bg-image.jpg');
  background-repeat: no-repeat;
  background-position: right bottom;
}

.header {
  position: relative;
  height: 442px;
  color: #fff;
  &__container {
    max-width: 1170px;
    margin: 0 auto;
    padding: 0 15px;
  }
}
</style>
