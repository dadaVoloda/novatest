<template>
  <div class="description">
    <img
      class="description__image"
      :src="require(`../assets/img/${description.image}`)"
      alt="poster"
    />
    <p class="description__text">
      {{ description.text }}
    </p>
  </div>
</template>

<script>
export default {
  inject: ['description'],
};
</script>

<style scoped lang="scss">
.description {
  display: flex;
  &__image {
    margin-right: 29px;
  }
  &__text {
    max-width: 462px;
    margin-top: 16px;
    line-height: 22px;
  }
}
</style>
