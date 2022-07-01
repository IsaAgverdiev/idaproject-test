<template>
  <div class="gallery">
    <div class="gallery__inner">
      <PhotoCard />
    </div>
  </div>
</template>

<script>
import PhotoCard from "./PhotoCard.vue";
export default { components: { PhotoCard } };
</script>

<style lang="scss">
@import "@/styles/main.scss";

.gallery {
  background: lightblue;
  flex-grow: 1;
}
</style>
