<template>
  <form class="form">
    <div class="form__item">
      <label class="form__label form__label--req">Наименование товара</label>
      <input
        type="text"
        class="form__input"
        placeholder="Введите наименование товара"
      />
    </div>
    <div class="form__item">
      <label class="form__label">Описание товара</label>
      <textarea
        class="form__input form__textarea"
        placeholder="Введите описание товара"
      ></textarea>
    </div>
    <div class="form__item">
      <label class="form__label form__label--req"
        >Ссылка на изображение товара</label
      >
      <input class="form__input" placeholder="Введите ссылку" />
    </div>
    <div class="form__item">
      <label class="form__label form__label--req">Цена товара</label>
      <input class="form__input" placeholder="Введите цену" />
    </div>
    <button class="form__btn btn">Добавить товар</button>
  </form>
</template>

<script>
export default {};
</script>

<style lang="scss">
@import "@/styles/main.scss";

.form {
  flex-basis: 332px;
  padding: 24px;
  margin-right: 15px;
  border-radius: 4px;
  filter: drop-shadow(0px 20px 30px rgba(0, 0, 0, 0.04)) drop-shadow(0px 6px 10px rgba(0, 0, 0, 0.02));
  background: #fff;

  &__item {
    display: flex;
    flex-direction: column;
    justify-content: start;
  filter: drop-shadow(0px 20px 30px rgba(0, 0, 0, 0.04)) drop-shadow(0px 6px 10px rgba(0, 0, 0, 0.02));

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
      top:0;
      width: 4px;
      height: 4px;
      background: $red;
      border-radius: 50%;
    }
  }

  &__input {
    padding: 16px 10px;
    border-radius: 4px;
    height: 36px;
    border: none;
    transition:0,3s;
  }

  &__input:focus {
    outline: 1px solid $text-placeholder;
    transition:0,3s;
  }

  &__input::placeholder {
    font-size: 12px;
    color: $text-placeholder;
    font-family: "Source Sans Pro", sans-serif;
  }

  &__textarea {
    width: 100%;
    height: 125px;
    resize: none;
  }

  &__btn {
    margin-top: 24px;
  }
}
</style>
