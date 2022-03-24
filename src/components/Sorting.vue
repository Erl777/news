<template>
  <span class="sorting">
    {{ todayDate }}
    <button class="sorting__btn" @click="$emit('toggle')">
      <img class="sorting__icon" :class="{ 'rotated': reversed }" src="/img/sort_icon.svg" alt="">
    </button>
  </span>
</template>

<script>
export default {
  name: "Sorting",
  props: {
    reversed: {
      type: Boolean,
      required: true
    }
  },
  computed: {
    todayDate() {
      const date = new Date()
      const locale = 'en-us';
      let options;
      if(document.body.clientWidth <= 375) options = { year: 'numeric', month: 'long', day: 'numeric' };
      else options = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' }
      return date.toLocaleDateString(locale, options)
    }
  }
}
</script>

<style scoped lang="scss">
  .sorting {
    display: flex;
    font-family: Arial, sans-serif;
    font-size: 16px;
    line-height: 25px;
    font-weight: 700;
    @media (max-width: 768px) {
      font-size: 12px;
    }
    &__btn {
      width: 24px;
      height: 24px;
      border: none;
      padding: 0;
      margin: 0 0 0 8px;
      background-color: transparent;
      &:hover {
        cursor: pointer;
      }
    }
    &__icon {
      transition: .3s ease-in-out;
      &.rotated {
        transform: rotate(180deg);
      }
    }
  }
</style>