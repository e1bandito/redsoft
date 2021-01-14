<template>
  <div class="contacts">
    <p class="contacts__phone">
      <img src="../assets/img/phone.svg" alt="phone-icon">
      <a href="tel:+74955555555" class="contacts__link">+7 (495) 555-55-55</a>
    </p>
    <p class="contacts__address">
      <img src="../assets/img/pin.svg" alt="map-pin">
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

    & img {
      display: block;
      margin-right: 8px;
    }
  }

  .contacts__address {
    display: flex;
    align-items: center;

    & img {
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
