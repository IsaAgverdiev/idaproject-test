<template>
  <div class="photo-card card">
    <div class="card__img-wrap">
      <img
        src="https://st.kp.yandex.net/images/film_iphone/iphone360_574182.jpg"
        class="card__img"
      />
    </div>
    <div class="card__inner">
      <h2 class="card__title">Наименование товара</h2>
      <p class="card__text">
        Довольно-таки интересное описание товара в несколько строк.
        Довольно-таки интересное описание товара в несколько строк
      </p>
      <p class="card__price">10 000 руб.</p>
    </div>
    <button class="card__delete-btn"></button>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss">
@import "@/styles/main.scss";

.card {
  max-width: 332px;
  width: 100%;
  min-height: 423px;
  background: #fff;
  position: relative;
  transition: 0.3s;

  &__inner {
    display: flex;
    height: calc(100% - 200px);
    flex-direction: column;
    justify-content: space-between;
    padding: 16px;
  }

  &__img-wrap {
    width: 100%;
    height: 200px;
  }

  &__img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  &__title {
    font-size: 20px;
    font-weight: 600;
    font-family: "Source Sans Pro", sans-serif;
    color: $text-color;
    margin-bottom: 16px;
  }

  &__text {
    font-size: 16px;
    font-family: "Source Sans Pro", sans-serif;
    color: $text-color;
    overflow: hidden;
    margin: 0;
  }

  &__price {
    font-size: 24px;
    font-weight: 600;
    font-family: "Source Sans Pro", sans-serif;
    color: $text-color;
    margin-top: 32px;
    margin-bottom: 0;
  }

  &__delete-btn {
    width: 32px;
    height: 32px;
    background: $red;
    position: absolute;
    outline: none;
    border: none;
    top: -16px;
    right: -16px;
    transition: 0.3s;
    border-radius: 10px;
    padding: 0;
    opacity: 0;
    // pointer-events: none;
    &::after {
      content: "";
      position: absolute;
      width: 16px;
      height: 16px;
      top: 50%;
      transform: translate(-50%, -50%);
      pointer-events: none;
      background: url("../assets/delete.png") no-repeat right center / contain;
    }
  }
}

.card:hover {
  .card__delete-btn {
    opacity: 1;
    pointer-events: auto;
    transition: 0.3s;
  }
}

.card__delete-btn:hover {
  cursor: pointer;
  background: lighten($red, 5);
}
</style>
