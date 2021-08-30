<template>
  <div class="navbar">
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
};
</script>

<style scoped lang="scss">
.navbar {
  &__logo {
    margin-bottom: 31px;
  }

  &__item {
    &:not(:last-child) {
      margin-bottom: 4px;
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
  }
}
</style>
