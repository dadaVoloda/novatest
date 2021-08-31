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
        <about-film @openModal="openModal"></about-film>
      </div>
    </main>
    <footer class="footer">
      <div class="footer__container">
        <ul class="footer__items">
          <li class="footer__item">
            <a href="#" class="footer__link"> Реклама </a>
          </li>
          <li class="footer__item">
            <a href="#" class="footer__link"> Условия использования </a>
          </li>
        </ul>
        <p class="footer__copyright">© 2003–2016 Spike</p>
      </div>
    </footer>
    <modal v-if="visibleModal" @close="closeModal" :modalPicture="modalPicture"></modal>
  </div>
</template>

<script>
import AboutFilm from './components/AboutFilm.vue';
import Modal from './components/Modal.vue';
import Movie from './components/Movie.vue';
import Navbar from './components/Navbar.vue';
export default {
  components: { Movie, Navbar, AboutFilm, Modal },
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
        {
          id: 1,
          image: 'picture1.jpg',
        },
        {
          id: 2,
          image: 'picture2.jpg',
        },
        {
          id: 3,
          image: 'picture3.jpg',
        },
        {
          id: 4,
          image: 'picture4.jpg',
        },
        {
          id: 5,
          image: 'picture5.jpg',
        },
        {
          id: 6,
          image: 'picture6.jpg',
        },
      ],
      visibleModal: false,
      modalPicture: '',
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
  methods: {
    openModal(item) {
      this.visibleModal = true;
      this.modalPicture = item;
    },
    closeModal() {
      this.visibleModal = false;
    },
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

.footer {
  &__container {
    display: flex;
    align-items: center;
    max-width: 780px;
    height: 58px;
    padding: 0 15px;
    margin: 0 auto;
    font-size: 14px;
    color: #fff;
  }

  &__items {
    display: flex;
    margin-left: auto;
  }

  &__item {
    margin-right: 17px;
  }

  &__link {
    transition: 0.25s;
    &:hover,
    &:focus {
      opacity: 0.6;
    }
  }
}
</style>
