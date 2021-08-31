<template>
  <div @click="$emit('close')" class="modal">
    <div @click.stop class="modal__body">
      <img :src="require(`../assets/img/${modalPicture}`)" alt="picture" />
    </div>
  </div>
</template>

<script>
export default {
  props: {
    modalPicture: {
      type: String,
      require: true,
    },
  },
};
</script>

<style scoped lang="scss">
.modal {
  position: relative;
  z-index: 5;
  position: fixed;
  display: flex;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.75);

  &__body {
    width: 400px;
    min-height: 400px;
    margin: auto;
    background-color: #fff;
    overflow: hidden;
    img {
      width: 100%;
      object-fit: cover;
    }
  }
}
</style>
