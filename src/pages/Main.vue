<template>
  <Header />
  <section class="main">
    <div class="container">
      <div class="main__inner">
        <FormAddPhoto @addPhoto="addPhoto" />
        <GalleryPhoto :photos="this.photos" @photoDelete="deletePhoto" />
      </div>
    </div>
  </section>
</template>

<script>
import Header from "@/components/Header.vue";
import FormAddPhoto from "@/components/FormAddPhoto.vue";
import GalleryPhoto from "@/components/GalleryPhoto.vue";
export default {
  components: { Header, FormAddPhoto, GalleryPhoto },
  data() {
    return {
      photos: [
        {
          src: "https://st.kp.yandex.net/images/film_iphone/iphone360_574182.jpg",
          title: "Наименование товара",
          text: "Довольно-таки интересное описание товара в несколько строк. Довольнотаки интересное описание товара в несколько строк",
          price: "10 000 руб.",
          id: new Date(),
        },
      ],
    };
  },

  methods: {
    addPhoto(photo) {
      this.photos.push(photo);
    },

    deletePhoto(photoID) {
      this.photos = this.photos.filter(function (card) {
        return card.id !== photoID;
      });
    },
  },
};
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
