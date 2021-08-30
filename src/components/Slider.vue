<template>
  <div class="slider">
    <div class="slider__wrapper">
      <ul ref="slider" class="slider__list" :class="{ transition: transition }">
        <li class="slider__item" v-for="item in pictures" :key="item">
          <img :src="require(`../assets/img/${item}`)" alt="image" />
          <button class="slider__item-btn" type="button">
            <img src="../assets/img/zoom.png" alt="zoom icon" />
          </button>
        </li>
      </ul>
    </div>
    <button @click="switchSlide('prev')" class="slider__btn slider__btn--prev" type="button">
      <img src="../assets/img/prev.png" alt="prev icon" />
    </button>
    <button @click="switchSlide('next')" class="slider__btn slider__btn--next" type="button">
      <img src="../assets/img/next.png" alt="next icon" />
    </button>
  </div>
</template>

<script>
export default {
  inject: ['pictures'],
  data() {
    return {
      index: 0,
      visibleSlides: 3,
      sliderWidth: null,
      slideWidth: null,
      initialPosition: null,
      transition: false,
    };
  },
  methods: {
    switchSlide(arg) {
      this.transition = true;
      const slider = this.$refs.slider;
      this.initialPosition = slider.offsetLeft;
      if (arg === 'next') {
        slider.style.left = `${this.initialPosition - this.slideWidth}px`;
        this.index++;
      } else {
        slider.style.left = `${this.initialPosition + this.slideWidth}px`;
        this.index--;
      }
    },
    checkIndex() {
      const slider = this.$refs.slider;
      const length = this.pictures.length;
      if (this.index < 0) {
        this.transition = false;
        slider.style.left = `-${(length - this.visibleSlides) * this.slideWidth}px`;
        this.index = length - this.visibleSlides;
      }
      if (this.index > length - this.visibleSlides) {
        this.transition = false;
        slider.style.left = '0px';
        this.index = 0;
      }
    },
  },
  mounted() {
    this.sliderWidth = this.$refs.slider.offsetWidth;
    this.slideWidth = this.sliderWidth / this.pictures.length;
  },
  watch: {
    index() {
      this.checkIndex();
    },
  },
};
</script>

<style scoped lang="scss">
.slider {
  position: relative;
  padding: 68px 0;

  &__wrapper {
    position: relative;
    max-width: 585px;
    height: 184px;
    margin: 0 auto;
    overflow: hidden;
  }

  &__list {
    position: absolute;
    top: 0;
    left: 0;
    display: flex;
    &.transition {
      transition: 0.3s;
    }
  }

  &__item {
    min-width: 165px;
    position: relative;
    margin: 0 15px;
    &:hover {
      .slider__item-btn {
        opacity: 1;
      }
    }
  }

  &__item-btn {
    display: flex;
    align-items: center;
    justify-content: center;
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(86, 58, 58, 0.5);
    opacity: 0;
    transition: 0.25s;
  }

  &__btn {
    position: absolute;
    top: 50%;
    left: 33px;
    transform: translateY(-50%);
    transition: 0.25s;
    &:hover,
    &:focus {
      opacity: 0.6;
    }

    &--next {
      left: auto;
      right: 33px;
    }
  }
}
</style>
