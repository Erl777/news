<template>
  <div class="card">
    <img class="card__img" :src="card.img" alt="">
    <p class="card__title">
      {{ card.title }}
    </p>
    <div class="card__info">
      <span class="date">
        {{ card.date }}
      </span>
      <span class="source">
        {{ card.source }}
      </span>
    </div>
    <p class="card__content">
      {{ card.content | truncate }}
    </p>
    <a :href="card.url" class="card__link">read more</a>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    card: {
      type: Object,
      required: true
    }
  },
  filters: {
    truncate: (input) => input.length > 280 ? `${input.substring(0, 280)}...` : input,
  }
}
</script>

<style scoped lang="scss">
@import "src/assets/style/var";
  .card {
    &__img {
      width: 100%;
      border-radius: 8px;
      margin: 0 0 16px 0;
      max-height: 176px;
      @media (max-width: 768px) {
        min-height: 128px;
      }
      @media (max-width: 550px) {
        min-height: 96px;
        margin: 0 0 8px;
      }
    }
    &__title {
      font-family: $playfair;
      font-weight: 700;
      font-size: 24px;
      margin: 0 0 24px;
      @media (max-width: 768px) {
        font-size: 18px;
        margin: 0 0 16px;
      }
      @media (max-width: 550px) {
        font-size: 16px;
        line-height: 21px;
        margin: 0 0 12px;
      }
    }
    &__info {
      display: flex;
      margin-bottom: 8px;
      @media (max-width: 768px) {
        margin: 0 0 16px;
      }
      @media (max-width: 550px) {
        font-size: 12px;
        margin: 0 0 8px;
      }
    }
    &__content, &__link {
      font-family: $playfair;
      font-size: 14px;
      color: $black60;
      margin: 0;
    }
    &__link {
      text-decoration: none;
      transition: .3s color ease-in-out;
      &:hover {
        color: cornflowerblue;
      }
    }
  }
  .date, .source {
    font-size: 12px;
    font-family: $roboto;
    font-weight: 400;
    color: $black20;
    &:not(:last-child) {
      margin-right: 16px;
    }
    @media (max-width: 550px) {
      font-size: 8px;
    }
  }
</style>