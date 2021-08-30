<template>
  <div>
    <header class="header">
      <div class="header__container">
        <movie class="header__component" :movie="movie"></movie>
        <navbar class="header__component" :links="links"></navbar>
      </div>
      <img class="header__img" src="./assets/img/deadpool.jpg" alt="deadpool" />
    </header>
    <main class="main">
      <div class="main__container">
        <about-film></about-film>
      </div>
    </main>
    <footer></footer>
  </div>
</template>

<script>
import AboutFilm from './components/AboutFilm.vue';
import Movie from './components/Movie.vue';
import Navbar from './components/Navbar.vue';
export default {
  components: { Movie, Navbar, AboutFilm },
  data() {
    return {
      movie: {
        title: 'Deadpool',
        year: 2016,
        country: 'usa',
        premission: '18+',
      },
      links: ['Все кино', 'Рейтинги', 'Общение', 'Войти'],
      descriptionFilm: {
        text:
          'Уэйд Уилсон — наёмник. Будучи побочным продуктом программы вооружённых сил под названием «Оружие X», Уилсон приобрёл невероятную силу, проворство и способность к исцелению. Но страшной ценой: его клеточная структура постоянно меняется, а здравомыслие сомнительно. Всё, чего Уилсон хочет, — это держаться на плаву в социальной выгребной яме. Но течение в ней слишком быстрое.',
        image: 'poster.jpg',
      },
      movieReviews: [
        { title: 'положительных', amount: 266 },
        { title: 'нейтральная', amount: 41 },
        { title: 'отрицательных', amount: 66 },
      ],
      videoInfo: {
        preview: 'preview.jpg',
        url: 'https://www.youtube.com/embed/FyKWUTwSYAs',
      },
      sliderPictures: [
        'picture1.jpg',
        'picture2.jpg',
        'picture3.jpg',
        'picture4.jpg',
        'picture5.jpg',
        'picture6.jpg',
      ],
    };
  },
  provide() {
    return {
      description: this.descriptionFilm,
      reviews: this.movieReviews,
      video: this.videoInfo,
      pictures: this.sliderPictures,
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

.main {
  max-width: 780px;
  padding: 0 15px;
  margin: 0 auto;
  &__container {
    background-color: $light-bg;
  }
}
</style>
