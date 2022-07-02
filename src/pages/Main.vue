<template>
  <Header @filtred="filtredPhotos" />
  <section class="main">
    <div class="container">
      <div class="main__inner">
        <FormAddPhoto @addPhoto="addPhoto" />
        <GalleryPhoto :photos="this.photosFilterd" @photoDelete="deletePhoto" />
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
          src: "https://res.cloudinary.com/practicaldev/image/fetch/s--gJHYh967--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://thepracticaldev.s3.amazonaws.com/i/i380o932dazhoyeazca0.png",
          title: "Isa Agverdiev",
          text: `Лучший разработчик, которого вы можете нанять. Красивый, обаятельный, иногда даже умный. Пишет сначала рабочий код, а потом оптимизированый!`,
          price: 60000,
          id: new Date(),
        },
      ],
      photosFilterd: [],
    };
  },

  computed: {
    filtredMin: function (array) {
      array = [...this.photos];
      return array.sort((a, b) => {
        let x = a.price;
        let y = b.price;
        return x < y ? -1 : x > y ? 1 : 0;
      });
    },
    filtredMax: function (array) {
      array = [...this.photos];
      return array.sort((a, b) => {
        let x = a.price;
        let y = b.price;
        return x > y ? -1 : x < y ? 1 : 0;
      });
    },
  },

  watch: {
    photos: {
      handler(val) {
        this.photosFilterd = val;
      },
      deep: true,
    },
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

    filtredPhotos(filter) {
      switch (filter) {
        case "default":
          this.photosFilterd = this.photos;
          break;
        case "min":
          this.photosFilterd = this.filtredMin;
          break;
        case "max":
          this.photosFilterd = this.filtredMax;
          break;

        default:
          break;
      }
    },
  },

  mounted() {
    this.$nextTick(function () {
      this.photosFilterd = this.photos;
    });
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
