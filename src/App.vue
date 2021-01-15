<template>
  <div id="app">
    <Sprite/>
    <Header/>
    <Footer/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Footer from "@/components/Footer";
import Sprite from "@/components/Sprite";

export default {
  name: 'App',
  components: {
    Sprite,
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
