<template>
  <div class="logo">
    <a href="#" class="logo__link">
      <svg width="48" height="48">
        <use xlink:href="../assets/img/sprite.svg#logo"/>
      </svg>
  </a>
  </div>
</template>

<script>
export default {
  name: "Logo"
}
</script>

<style lang="scss">
  @import "src/assets/styles/variables";

  .logo {
    margin-right: 24px;
    margin-top: 6px;
  }

  .logo__link {
    display: block;
  }
</style>
