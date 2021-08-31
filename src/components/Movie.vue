<template>
  <div class="movie">
    <h1 class="movie__title">{{ movie.title }}</h1>
    <p>{{ movie.year }}</p>
    <p>{{ movie.country }}</p>
    <p class="movie__premission">{{ movie.premission }}</p>
  </div>
</template>

<script>
export default {
  props: {
    movie: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style scoped lang="scss">
.movie {
  font-family: 'BebasNeueRegular', sans-serif;
  font-size: 40px;
  text-transform: uppercase;
  @media (max-width: 768px) {
    font-size: 30px;
  }
  &__title {
    font-size: 100px;
    line-height: 73px;
    margin-bottom: 8px;
    font-weight: normal;
    @media (max-width: 768px) {
      font-size: 70px;
      line-height: 50px;
    }
    @media (max-width: 375px) {
      font-size: 56px;
      line-height: 40px;
    }
  }
  &__premission {
    color: $pink;
  }
}
</style>
