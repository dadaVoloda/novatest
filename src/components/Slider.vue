<template>
  <div class="slider">
    <div class="slider__wrapper">
      <ul ref="slider" class="slider__list" :class="{ transition: transition }">
        <slide
          v-for="item in pictures"
          :key="item.id"
          :item="item"
          @open="$emit('open', item)"
        ></slide>
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
import Slide from './Slide.vue';
export default {
  components: { Slide },
  inject: ['pictures'],
  data() {
    return {
      index: 0,
      visibleSlides: 3,
      sliderWidth: null,
      slideWidth: null,
      initialPosition: null,
      transition: false,
      width: 0,
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
    this.width = window.innerWidth;
    if (this.width <= 768) {
      this.visibleSlides = 2;
    }
    if (this.width <= 500) {
      this.visibleSlides = 1;
    }
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
    @media (max-width: 768px) {
      max-width: 390px;
    }
    @media (max-width: 500px) {
      max-width: 195px;
    }
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

  &__btn {
    position: absolute;
    top: 50%;
    left: 33px;
    transform: translateY(-50%);
    transition: 0.25s;
    @media (max-width: 550px) {
      left: 15px;
    }
    &:hover,
    &:focus {
      opacity: 0.6;
    }

    &--next {
      left: auto;
      right: 33px;
      @media (max-width: 550px) {
        right: 15px;
      }
    }
  }
}
</style>
