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
  @media (max-width: 992px) {
    padding: 40px 20px;
    flex-wrap: wrap;
  }
  @media (max-width: 768px) {
    padding: 30px 15px;
  }
  @media (max-width: 500px) {
    align-items: flex-start;
  }
  @media (max-width: 375px) {
    padding: 30px 10px;
  }
  &__title {
    margin-right: 60px;
    font-size: 24px;
    @media (max-width: 768px) {
      margin: 10px 30px 10px 0;
    }
    @media (max-width: 500px) {
      margin: 0px 30px 0px 0;
    }
    @media (max-width: 375px) {
      margin-right: 15px;
    }
  }
  &__list {
    display: flex;
    flex-wrap: wrap;
    @media (max-width: 500px) {
      flex-direction: column;
    }
  }
  &__item {
    position: relative;
    z-index: 1;
    width: 135px;
    display: flex;
    flex-direction: column;
    @media (max-width: 768px) {
      margin-bottom: 10px;
    }
    @media (max-width: 500px) {
      margin-bottom: 0;
      flex-direction: row;
      span {
        &:not(:last-child) {
          margin-right: 10px;
          @media (max-width: 375px) {
            margin-right: 6px;
          }
        }
      }
    }
    &:not(:last-child) {
      margin-right: 60px;
      @media (max-width: 768px) {
        margin-right: 30px;
      }
      @media (max-width: 500px) {
        margin-bottom: 10px;
      }
    }
    &::before {
      position: absolute;
      content: '';
      width: 109px;
      height: 100%;
      left: -2px;
      background-color: #b7ffb1;
      z-index: -1;
      @media (max-width: 500px) {
        width: 100px;
        opacity: 0.6;
      }
    }
    &:nth-child(2) {
      &::before {
        width: 22px;
        background-color: #d7d7d7;
        @media (max-width: 500px) {
          width: 100px;
        }
      }
    }
    &:nth-child(3) {
      &::before {
        width: 33px;
        background-color: #ffb1b1;
        @media (max-width: 500px) {
          width: 100px;
        }
      }
    }
  }
}
</style>
