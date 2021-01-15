<template>
  <button class="btn"
          :class="classes"
          :disabled="disabled"
          :state="state"
          @click="click"
  >
    <span class="btn__inner"
      v-if="state === 'default'"
    >
      {{ btnValue }}
    </span>
    <span class="btn__inner"
      v-if="state === 'inCart'"
    >
      <svg width="14" height="14">
        <use xlink:href="#icon_check"/>
      </svg>
      В корзине
    </span>
    <span class="btn__inner btn__inner--loader"
          v-if="state === 'inProgress'"
    >
      <svg width="22" height="22">
        <use xlink:href="#icon_loader"/>
      </svg>
    </span>
  </button>

</template>

<script>
export default {
  name: "Btn",
  props: {
    classes: String,
    btnValue: String,
    btnType: String,
    disabled: Boolean,
    state: String
  },
  methods: {
    click() {
      this.$emit('click');
    }
  }
}
</script>

<style lang="scss">
  @import "src/assets/styles/variables";

  .btn {
    font-family: "Merriweather", "Arial", sans-serif;
    display: inline-block;
    align-items: center;
    justify-content: center;
    border: none;
    background-color: $main;
    appearance: none;
    min-width: 112px;
    min-height: 48px;
    color: $white;
    cursor: pointer;
    transition: background-color 0.3s;
    padding: 8px;
    margin: 0;

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

  .btn__inner {
    display: flex;
    align-items: center;
    justify-content: center;

    & svg {
      margin-right: 4px;
      fill: $white;
    }

    &--loader svg {
      animation: loading 2s infinite linear;
      margin-right: 0;
    }
  }

  @keyframes loading {
    0% {
      transform: rotate(0);
    }
    100% {
      transform: rotate(360deg);
    }
  }
</style>
