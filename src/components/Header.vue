<template>
  <div class="header">
    <div class="container">
      <div class="header__inner">
        <Logo/>
        <Nav/>
        <Search/>
      </div>
    </div>
  </div>
</template>

<script>
import Logo from "@/components/Logo";
import Nav from "@/components/Nav";
import Search from "@/components/Search";
export default {
  name: 'Header',
  components: {Search, Nav, Logo},
}
</script>

<style lang="scss">
  @import "src/assets/styles/variables";
  @import "src/assets/styles/scaffolding";

  .header {
    padding: 18px 0 17px;
    border-bottom: 1px solid $border-light;
  }

  .header__inner {
    display: flex;
    align-items: center;
    flex-wrap: wrap;
  }
</style>
