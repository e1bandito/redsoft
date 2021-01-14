<template>
  <button class="btn"
          :class="classes"
          :type="btnType"
          :disabled="disabled"
  >{{ btnValue }}</button>
</template>

<script>
export default {
  name: "Btn",
  props: {
    classes: String,
    btnValue: String,
    btnType: String,
    disabled: Boolean
  }
}
</script>

<style lang="scss">
  @import "src/assets/styles/variables";

  .btn {
    font-family: "Merriweather", "Arial", sans-serif;
    display: inline-block;
    border: none;
    background-color: $main;
    appearance: none;
    min-width: 112px;
    min-height: 48px;
    color: $white;
    cursor: pointer;
    transition: background-color 0.3s;

    &:hover {
      background-color: $hover;
    }

    &:disabled {
      background-color: $disabled;
      cursor: not-allowed;
    }

    &--in-cart {
      background-color: $in-cart;
    }

    &--search {
      min-width: 122px;
    }
  }
</style>
