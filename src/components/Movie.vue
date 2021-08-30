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
  &__title {
    font-size: 100px;
    line-height: 73px;
    margin-bottom: 8px;
    font-weight: normal;
  }
  &__premission {
    color: $pink;
  }
}
</style>
