<template>
  <header class="header container">
    <div class="logo">
      <a class="logo__link" href="#">
        News <span>Portal</span>
      </a>
    </div>
    <div class="search">
      <transition name="fade">
        <input
            id="search"
            v-show="showInput"
            class="search__input"
            type="text"
            @input="$emit('input', $event.target.value)"
        >
      </transition>
      <button @click="showSearch" class="search__btn">
        <img class="search__icon" src="/img/search_icon.svg" alt="">
      </button>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      showInput: false
    }
  },
  methods: {
    showSearch() {
      this.showInput = true;
      this.$nextTick(() => document.getElementById('search').focus())
      document.addEventListener('click', this.hideSearch)
    },
    hideSearch(e) {
      if(!e.target.classList.contains('search__input') && !e.target.classList.contains('search__btn')) this.showInput = false
    }
  },
  beforeDestroy() {
    document.removeEventListener('click', this.hideSearch)
  }
}
</script>

<style scoped lang="scss">
  @import "/src/assets/style/var";

  .header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 72px;
    @media (max-width: 768px) {
      margin-bottom: 48px;
    }
    @media (max-width: 375px) {
      margin-bottom: 40px;
    }
  }

  .logo {
    position: relative;
    left: -10px;
    width: 56px;
    max-width: 56px;
    height: 37px;
    padding: 8px;
    border-radius: 4px;
    background: $black80;
    font-family: $playfair;
    font-weight: 700;
    font-size: 16px;
    color: $white;
    text-decoration: none;
    @media (max-width: 1280px) {
      left: unset;
    }
    &__link {
      position: absolute;
      top: 8px;
      left: 8px;
      display: flex;
      text-decoration: none;
      color: $white;
      span {
        color: $black80;
        margin-left: 18px;
      }
    }
  }
  .search {
    position: relative;
    &__btn {
      padding: 0;
      margin: 0;
      border: none;
      background-color: transparent;
      &:hover {
        cursor: pointer;
      }
    }
    &__input {
      position: absolute;
      left: -10px;
      top: 0;
      height: 24px;
      border-radius: 4px;
      transform: translateX(-100%);
    }
    &__icon {
      pointer-events: none;
    }
  }

  .fade-enter-active, .fade-leave-active {
    -webkit-transition: $transition;
    -o-transition: $transition;
    transition: $transition;
  }

  .fade-enter, .fade-leave-to {
    opacity: 0;
  }

</style>