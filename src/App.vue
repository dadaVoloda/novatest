<template>
  <div>
    <header class="header">
      <div class="header__container">
        <movie class="header__component" :movie="movie"></movie>
        <navbar class="header__component" :links="links"></navbar>
      </div>
      <img class="header__img" src="./assets/img/deadpool.jpg" alt="deadpool" />
    </header>
    <main></main>
    <footer></footer>
  </div>
</template>

<script>
import Movie from './components/Movie.vue';
import Navbar from './components/Navbar.vue';
export default {
  components: { Movie, Navbar },
  data() {
    return {
      movie: {
        title: 'Deadpool',
        year: 2016,
        country: 'usa',
        premission: '18+',
      },
      links: ['Все кино', 'Рейтинги', 'Общение', 'Войти'],
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
    display: flex;
    justify-content: space-between;
    padding-top: 50px;
  }
  &__component {
    position: relative;
    z-index: 1;
  }
  &__img {
    position: absolute;
    bottom: 0;
    left: 50%;
    transform: translateX(-50%);
  }
}
</style>
