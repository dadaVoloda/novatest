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
  @media (max-width: 500px) {
    flex-direction: column;
  }
  &__image {
    margin-right: 29px;
    height: 241px;
    @media (max-width: 768px) {
      margin-right: 15px;
    }
    @media (max-width: 500px) {
      margin-right: 0;
      margin-top: 15px;
      object-fit: contain;
    }
  }
  &__text {
    max-width: 462px;
    margin-top: 16px;
    line-height: 22px;
    @media (max-width: 768px) {
      max-width: 100%;
      padding: 0 5px;
    }
    @media (max-width: 500px) {
      padding: 0 10px;
    }
  }
}
</style>
