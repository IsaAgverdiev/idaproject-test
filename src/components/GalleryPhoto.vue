<template>
  <div class="gallery">
    <transition-group name="list" tag="div" class="gallery__inner">
      <h1 v-if="!photos.length">
        Фотокарточки отсутсвую! Добавьте карточку, используя форму
      </h1>
      <PhotoCard
        v-for="photo in photos"
        :key="photo.id"
        :photo="photo"
        @deletePhoto="deletePhoto"
      />
    </transition-group>
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

  methods: {
    deletePhoto(photoID) {
      this.$emit("photoDelete", photoID);
    },
  },
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
