<template>
  <div id="app">
    <Header/>
    <Footer/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Footer from "@/components/Footer";

export default {
  name: 'App',
  components: {
    Footer,
    Header
  }
}
</script>

<style lang="scss">
  #app {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
  }
</style>
