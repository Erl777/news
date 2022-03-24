<template>
  <div id="app">
    <Header v-model="searchValue" />
    <main class="main container">
      <Home :search-value="searchValue" />
    </main>
    <Footer />
  </div>
</template>

<script>
import Home from "@/components/Home";
import Header from "@/components/Header";
import Footer from "@/components/Footer";

export default {
  name: 'App',
  components: {
    Header,
    Home,
    Footer
  },
  data() {
    return {
      searchValue: ''
    }
  }
}
</script>

<style lang="scss">
  #app {
    position: relative;
    padding-top: 32px;
    @media (max-width: 1280px){
      padding: 32px 60px 0;
    }
    @media (max-width: 550px) {
      padding: 32px 35px 0;
    }
  }
  .container {
    width: 100%;
    max-width: 1170px;
    margin: 0 auto;
  }
  .main {
    padding-bottom: 173px;
  }
</style>
