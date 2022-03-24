<template>
 <footer class="footer">
   <span class="copyright">Copyright 2022 News Portal</span>
 </footer>
</template>

<script>
export default {
  name: "Footer"
}
</script>

<style scoped lang="scss">
@import "src/assets/style/var";
  .footer {
    width: 100%;
    height: 83px;
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: $white;
    @media (max-width: 1280px){
      position: absolute;
      left: 0;
      bottom: 0;
    }
  }
  .copyright {
    font-family: $playfair;
    font-weight: 700;
    color: $black20;
  }
</style>