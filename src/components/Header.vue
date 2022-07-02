<template>
  <header class="header">
    <div class="container">
      <div class="header__inner">
        <h1 class="header__title title">Добавление товара</h1>
        <select class="header__filter filter" @change="onChange">
          <option value="default" selected>По-умолчанию</option>
          <option value="min">По цене min</option>
          <option value="max">По цене max</option>
        </select>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  methods: {
    onChange(event) {
      this.$emit("filtred", event.target.value);
    },
  },
};
</script>

<style lang="scss">
@import "@/styles/main.scss";

.header {
  padding: 30px 0;

  &__inner {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  &__filter {
    display: inline-block;
    font-size: 12px;
    color: $text-placeholder;
    max-width: 122px;
    width: 100%;
    height: 36px;
    padding-left: 16px;
    border-radius: 4px;
    border: 1px solid #b4b4b4;
    outline: none;
    font-family: "Source Sans Pro", sans-serif;

    -webkit-appearance: none;
    -moz-appearance: none;
    appearance: none;
  }

  &__filter:after {
    content: "";
    display: block;
    width: 4.59px;
    height: 4.59px;
    position: absolute;
    right: 0px;
    top: 0px;
    background: url("../assets/select-icon.png") no-repeat right center / cover;
    opacity: 0.6;
    transition: all 0.27s ease-in-out;
    transform: rotate(0deg);
  }
}
</style>
