<template>
  <div class="contacts">
    <p class="contacts__phone">
      <svg width="14" height="14">
        <use xlink:href="#icon_phone"/>
      </svg>
      <a href="tel:+74955555555" class="contacts__link">+7 (495) 555-55-55</a>
    </p>
    <p class="contacts__address">
      <svg width="14" height="14">
        <use xlink:href="#icon_pin"/>
      </svg>
      г. Москва, ул. Расплетина, 24
    </p>
  </div>
</template>

<script>
export default {
  name: "Contacts"
}
</script>

<style lang="scss">
  @import "src/assets/styles/variables";

  .contacts {
    margin-left: auto;
    display: flex;
  }

  .contacts__phone {
    display: flex;
    align-items: center;
    margin-right: 55px;

    & svg {
      display: block;
      margin-right: 8px;
    }
  }

  .contacts__address {
    display: flex;
    align-items: center;

    & svg {
      display: block;
      margin-right: 8px;
    }
  }

  .contacts__link {
    color: $text-dark-brown;
    transition: color 0.3s;

    &:hover {
      color: $hover-light;
    }
  }
</style>
