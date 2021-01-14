<template>
  <nav class="nav">
    <ul class="nav__list">
      <li class="nav__item"
          v-for="(item, index) in navItems"
          :key="index">
        <a :href="item.link" class="nav__link">
          {{ item.title }}
        </a>
      </li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: "Nav",
  data () {
    return {
      navItems: [
        {
          title: 'Каталог',
          link: '#',
        },
        {
          title: 'Доставка',
          link: '#',
        },
        {
          title: 'Оплата',
          link: '#',
        },
        {
          title: 'Контакты',
          link: '#',
        },
        {
          title: 'О галерее',
          link: '#',
        }
      ]
    }
  }
}
</script>

<style lang="scss">
  @import "src/assets/styles/variables";

  .nav__list {
    list-style: none;
    padding: 0;
    margin: 0;
    display: flex;
  }

  .nav__link {
    font-size: 14px;
    line-height: 1.5;
    padding: 12px;
    margin: 0 12px;
    color: $text-brown;
    transition: color 0.3s;

    &:hover {
      color: $hover;
    }
  }
</style>
