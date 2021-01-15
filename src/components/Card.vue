<template>
  <article class="card"
    :class="item.state === 'sold' ? 'card--sold' : ''"
  >
    <div class="card__img">
      <picture>
        <source type="image/webp" :srcset="getUrl(item.img.webp2x) + ' 2x, ' + getUrl(item.img.webp) + ' 1x'">
        <source :srcset="getUrl(item.img.jpg2x) + ' 2x, ' + getUrl(item.img.jpg) + ' 1x'">
        <img :src="getUrl(item.img.jpg)" :alt="item.title">
      </picture>

    </div>
    <div class="card__wrap">
      <h2 class="card__title">{{ item.title }}</h2>
      <div class="card__footer">
        <div class="card__price">
          <p class="card__old-price"
            v-if="item.state !== 'sold'"
          >{{ item.price.old }}</p>
          <p class="card__actual-price"
             v-if="item.state !== 'sold'"
          >{{ item.price.actual }}</p>
          <p class="card__sold"
            v-if="item.state === 'sold'"
          >Продана на аукционе</p>
        </div>
        <Btn
            v-if="item.state !== 'sold'"
            :class="item.state === 'inCart' ? 'btn--in-cart' : ''"
            :state="item.state"
            btnValue="Купить"
            @click="getClick(index)"
        />
      </div>
    </div>
  </article>
</template>

<script>
import Btn from "@/components/Btn";
export default {
  name: "Card",
  components: {Btn},
  props: {
    item: Object,
    index: Number
  },
  methods: {
    getUrl(pic) {
      return require(`../assets/img/${pic}`);
    },
    getClick(index) {
      console.log(index);
    }
  }
}
</script>

<style lang="scss">
  @import "src/assets/styles/variables";

  .card {
    width: 100%;
    border: 1px solid $border-light;
    height: 100%;
    display: flex;
    flex-direction: column;

    &--sold {
      opacity: 0.5;

      &:hover {
        cursor: not-allowed;
      }
    }
  }

  .card__wrap {
    padding: 14px 24px 22px;
    flex-grow: 1;
    display: flex;
    flex-direction: column;
  }

  .card__footer {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-top: auto;
    min-height: 48px;
  }

  .card__title {
    margin: 0 0 23px 0;
    font-size: 18px;
    font-weight: 400;
    color: $text-brown;
  }

  .card__actual-price {
    margin: 0;
    font-size: 16px;
    color: $text-brown;
    font-weight: 700;
  }

  .card__old-price {
    margin: 0;
    font-weight: 300;
    color: $text-lighter-grey;
    text-decoration: line-through;
  }

  .card__sold {
    margin: 0;
    font-size: 16px;
    font-weight: 700;
    color: $text-brown;
  }
</style>
