<template>
  <div class="video">
    <div v-show="!isVideoShow" class="video__image-block">
      <img class="video__image" :src="require(`../assets/img/${video.preview}`)" alt="preview" />
      <button class="video__btn" @click="showVideo" type="button">
        <img src="../assets/img/play.png" alt="play" />
      </button>
    </div>
    <iframe
      v-show="isVideoShow"
      class="video__iframe"
      src="https://www.youtube.com/embed/FyKWUTwSYAs"
      title="YouTube video player"
      frameborder="0"
      allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
      allowfullscreen
    ></iframe>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isVideoShow: false,
    };
  },
  inject: ['video'],
  methods: {
    showVideo() {
      this.isVideoShow = true;
    },
  },
};
</script>

<style scoped lang="scss">
.video {
  position: relative;
  display: flex;
  flex-direction: column;
  height: 422px;
  @media (max-width: 500px) {
    height: 300px;
  }
  @media (max-width: 375px) {
    height: 250px;
  }

  &__image-block {
    flex: 1;
  }

  &__image {
    height: 100%;
    object-fit: cover;
  }

  &__btn {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    transition: 0.25s;
    &:hover,
    &:focus {
      opacity: 0.7;
    }
  }

  &__iframe {
    width: 100%;
    height: 422px;
    @media (max-width: 500px) {
      height: 300px;
    }
    @media (max-width: 375px) {
      height: 250px;
    }
  }
}
</style>
