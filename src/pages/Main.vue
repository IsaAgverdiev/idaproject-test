<template>
  <Header />
  <section class="main">
    <div class="container">
      <div class="main__inner">
        <FormAddPhoto />
        <GalleryPhoto />
      </div>
    </div>
  </section>
</template>

<script>
import Header from "@/components/Header.vue";
import FormAddPhoto from "@/components/FormAddPhoto.vue";
import GalleryPhoto from "@/components/GalleryPhoto.vue";
export default { components: { Header, FormAddPhoto, GalleryPhoto } };
</script>

<style lang="scss">
@import "@/styles/main.scss";

.main {
  &__inner {
    display: flex;
    justify-content: space-between;
    &__inner:first-child {
      flex-grow: 0;
      flex-shrink: 1;
    }
  }
}
</style>
