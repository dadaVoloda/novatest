<template>
  <div class="navbar">
    <button class="navbar__close" type="button" @click="$emit('closeNav')">
      <span></span>
      <span></span>
    </button>
    <logo class="navbar__logo"></logo>
    <nav>
      <ul>
        <li class="navbar__item" v-for="item in links" :key="item">
          <a href="#" class="navbar__link"> {{ item }} </a>
        </li>
      </ul>
    </nav>
  </div>
</template>

<script>
import Logo from './Logo.vue';
export default {
  components: { Logo },
  props: {
    links: {
      type: Array,
      required: true,
    },
  },
  methods: {
    toggleNavbar() {
      this.$refs.btn.classList.toggle('active');
    },
  },
};
</script>

<style scoped lang="scss">
.navbar {
  @media (max-width: 768px) {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.95);
    z-index: 10;
    padding: 30px 15px;
  }

  &__close {
    position: absolute;
    z-index: 10;
    display: none;
    flex-direction: column;
    justify-content: space-between;
    width: 36px;
    height: 25px;
    right: 15px;
    top: 30px;
    @media (max-width: 768px) {
      display: flex;
    }
    span {
      width: 100%;
      height: 3px;
      background-color: #fff;
      &:first-child {
        transform: translateY(11px) rotate(-45deg);
      }
      &:last-child {
        transform: translateY(-11px) rotate(45deg);
      }
    }
  }

  &__logo {
    margin-bottom: 31px;
  }

  &__item {
    &:not(:last-child) {
      margin-bottom: 4px;
      @media (max-width: 768px) {
        margin-bottom: 10px;
      }
    }
  }

  &__link {
    width: 165px;
    height: 25px;
    text-align: center;
    font-size: 20px;
    background-color: $pink;
    transition: 0.25s;
    &:hover,
    &:focus {
      background-color: darken($pink, 7);
    }
    @media (max-width: 768px) {
      display: flex;
      justify-content: center;
      align-items: center;
      width: 100%;
      height: 50px;
      background-color: rgba(231, 30, 110, 0.4);
    }
  }
}
</style>
