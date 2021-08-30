<template>
  <div class="reviews">
    <p class="reviews__title">Рецензии:</p>
    <ul class="reviews__list">
      <li class="reviews__item" v-for="item in reviews" :key="item.title">
        <span>{{ item.amount }}</span>
        <span>{{ item.title }}</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  inject: ['reviews'],
};
</script>

<style scoped lang="scss">
.reviews {
  display: flex;
  align-items: center;
  padding: 38px 32px 39px;
  &__title {
    margin-right: 60px;
    font-size: 24px;
  }
  &__list {
    display: flex;
  }
  &__item {
    position: relative;
    z-index: 1;
    width: 135px;
    display: flex;
    flex-direction: column;
    &:not(:last-child) {
      margin-right: 60px;
    }
    &::before {
      position: absolute;
      content: '';
      width: 109px;
      height: 100%;
      left: -2px;
      background-color: #b7ffb1;
      z-index: -1;
    }
    &:nth-child(2) {
      &::before {
        width: 22px;
        background-color: #d7d7d7;
      }
    }
    &:nth-child(3) {
      &::before {
        width: 33px;
        background-color: #ffb1b1;
      }
    }
  }
}
</style>
