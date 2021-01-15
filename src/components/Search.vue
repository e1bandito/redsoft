<template>
  <div class="search">
    <form action="" class="search__form">
      <label class="search__label">
        <input type="text" class="search__input" placeholder="Поиск по названию картины">
      </label>
      <Btn
        :classes=btn.class
        :disabled=btn.disabled
        :state="'default'"
        btnValue="Найти"
      />
    </form>
  </div>
</template>

<script>
import Btn from "@/components/Btn";
export default {
  name: "Search",
  components: {Btn},
  data () {
    return {
      btn: {
        class: 'btn--search',
        disabled: false
      }
    }
  }
}
</script>

<style lang="scss">
  @import "src/assets/styles/variables";

  .search {
    width: 416px;
    margin-left: auto;
  }

  .search__form {
    display: flex;
  }

  .search__label {
    display: block;
    flex-grow: 1;
  }

  .search__input {
    font-family: "Merriweather", "Arial", sans-serif;
    font-size: 14px;
    line-height: 1.5;
    color: $text-brown;
    width: 100%;
    height: 48px;
    padding: 13px 16px 14px;
    background-color: $bg-light;
    border: 1px solid $border-light;
    border-right: none;
    border-radius: 0;
    box-shadow: none;
    appearance: none;

    &:hover {
      border-color: $border;
    }

    &:focus {
      border-color: $border;
      outline: none;
    }

    &::placeholder {
      color: $text-light-grey;
    }
  }

</style>
