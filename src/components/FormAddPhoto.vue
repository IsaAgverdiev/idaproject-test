<template>
  <form class="form" @submit.prevent="createCard">
    <div class="form__item">
      <label class="form__label form__label--req">Наименование товара</label>
      <input
        v-model="title"
        type="text"
        class="form__input"
        :class="{ showError: showError.title }"
        placeholder="Введите наименование товара"
      />
      <label
        class="form__label form__label--error"
        :class="{ showError: showError.title }"
        >Поле является обязательным</label
      >
    </div>
    <div class="form__item">
      <label class="form__label">Описание товара</label>
      <textarea
        v-model="text"
        class="form__input form__textarea"
        placeholder="Введите описание товара"
      ></textarea>
    </div>
    <div class="form__item">
      <label class="form__label form__label--req"
        >Ссылка на изображение товара</label
      >
      <input
        v-model="src"
        type="text"
        class="form__input"
        :class="{ showError: showError.src }"
        placeholder="Введите ссылку"
      />
      <label
        class="form__label form__label--error"
        :class="{ showError: showError.src }"
        >Поле является обязательным</label
      >
    </div>
    <div class="form__item">
      <label class="form__label form__label--req">Цена товара</label>
      <input
        v-model="price"
        type="number"
        class="form__input"
        :class="{ showError: showError.price }"
        placeholder="Введите цену"
      />
      <label
        class="form__label form__label--error"
        :class="{ showError: showError.price }"
        >Поле является обязательным</label
      >
    </div>
    <button class="form__btn btn" :class="{ active: btnActive }">
      Добавить товар
    </button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      title: "",
      text: "",
      src: "",
      price: "",
      btnActive: false,
      showError: {
        title: false,
        src: false,
        price: false,
      },
    };
  },

  methods: {
    createCard() {
      if (this.title !== "" && this.src !== "" && this.price !== "") {
        let photo = {
          title: this.title,
          text: this.text,
          src: this.src,
          price: this.price,
          id: new Date(),
        };

        this.$emit("addPhoto", photo);
      } else {
        this.showErrors();
      }
    },

    activateBtn() {
      if (this.title !== "" && this.src !== "" && this.price !== "") {
        this.btnActive = true;
      } else {
        this.btnActive = false;
      }
    },

    showErrors() {
      this.title == ""
        ? (this.showError.title = true)
        : (this.showError.title = false);

      this.src == ""
        ? (this.showError.src = true)
        : (this.showError.src = false);

      this.price == ""
        ? (this.showError.price = true)
        : (this.showError.price = false);
    },
  },

  watch: {
    title: function () {
      this.showError.title = false;
      this.activateBtn();
    },
    src: function () {
      this.showError.src = false;
      this.activateBtn();
    },
    price: function () {
      this.showError.price = false;
      this.activateBtn();
    },
  },
};
</script>

<style lang="scss">
@import "@/styles/main.scss";

.form {
  flex-basis: 332px;
  flex-shrink: 0;
  padding: 24px;
  margin-right: 15px;
  height: 440px;
  // max-height: 460px;
  border-radius: 4px;
  filter: drop-shadow(0px 20px 30px rgba(0, 0, 0, 0.04))
    drop-shadow(0px 6px 10px rgba(0, 0, 0, 0.02));
  background: #fff;

  &__item {
    display: flex;
    flex-direction: column;
    justify-content: start;
    filter: drop-shadow(0px 20px 30px rgba(0, 0, 0, 0.04))
      drop-shadow(0px 6px 10px rgba(0, 0, 0, 0.02));
  }

  &__item + &__item {
    margin-top: 16px;
  }

  &__label {
    font-size: 10px;
    color: $text-label;
    margin-bottom: 4px;
  }

  &__label--req {
    position: relative;
    &::after {
      content: "";
      position: absolute;
      top: 0;
      width: 4px;
      height: 4px;
      background: $red;
      border-radius: 50%;
    }
  }

  &__label--error {
    position: absolute;
    bottom: -16px;
    color: $red;
    margin-bottom: 2px;
    margin-top: 4px;
    opacity: 0;
    transition: 0.3s;

    &.showError {
      opacity: 1;
      transition: 0.3s;
    }
  }

  &__input {
    padding: 16px 10px;
    border-radius: 4px;
    height: 36px;
    border: none;
    transition: 0.3s;

    &.showError {
      outline: 1px solid $red;
    }
  }

  &__input:focus {
    outline: 1px solid $text-placeholder;
    transition: 0.3s;
  }

  &__input::placeholder {
    font-size: 12px;
    color: $text-placeholder;
    font-family: "Source Sans Pro", sans-serif;
  }

  &__textarea {
    width: 100%;
    height: 108px;
    resize: none;
  }

  &__btn {
    margin-top: 24px;
  }
}
</style>
