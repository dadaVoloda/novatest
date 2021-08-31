<template>
  <li class="slider__item">
    <img :src="require(`../assets/img/${item.image}`)" alt="image" />
    <button @click="$emit('open', item)" class="slider__item-btn" type="button">
      <img src="../assets/img/zoom.png" alt="zoom icon" />
    </button>
  </li>
</template>

<script>
export default {
  props: {
    item: {
      type: Object,
      require: true,
    },
  },
};
</script>

<style scoped lang="scss">
.slider {
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
}
</style>
