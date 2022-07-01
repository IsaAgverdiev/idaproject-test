<template>
  <div class="gallery">
    <div class="gallery__inner">
      <PhotoCard v-for="photo in photos" :key="photo.id" :photo="photo" />
    </div>
  </div>
</template>

<script>
import PhotoCard from "./PhotoCard.vue";
export default {
  components: { PhotoCard },
  props: ["photos"],

  data() {
    return {};
  },

  methods: {},
};
</script>

<style lang="scss">
@import "@/styles/main.scss";

.gallery {
  flex-grow: 1;

  &__inner {
    display: flex;
    gap: 16px;
    flex-wrap: wrap;
  }
}
</style>
