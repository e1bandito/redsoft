<template>
  <div id="app">
    <Sprite/>
    <Header/>
    <section class="products">
      <div class="container">
        <h1 class="products__title">Картины эпохи Возрождения</h1>
        <ul class="products__list">
          <li class="products__item"
            v-for="(item, index) in products"
            :key="index"
          >
            <Card
              :item=item
              :index="index"
              @click="getProduct"
            />
          </li>
        </ul>
      </div>
    </section>
    <Footer/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Footer from "@/components/Footer";
import Sprite from "@/components/Sprite";
import Card from "@/components/Card";
import axios from "axios";

export default {
  name: 'App',
  components: {
    Card,
    Sprite,
    Footer,
    Header
  },
  data() {
    return {
      products: [
        {
          img: {
            jpg: 'cards/1.jpg',
            jpg2x: 'cards/1@2x.jpg',
            webp: 'cards/1.webp',
            webp2x: 'cards/1@2x.webp'
          },
          title: '«Рождение Венеры» Сандро Боттичелли',
          price: {
            actual: '1 000 000 $',
            old: '2 000 000 $'
          },
          state: 'default'
        },
        {
          img: {
            jpg: 'cards/2.jpg',
            jpg2x: 'cards/2@2x.jpg',
            webp: 'cards/2.webp',
            webp2x: 'cards/2@2x.webp'
          },
          type: 'jpg',
          title: '«Тайная вечеря»  Леонардо да Винчи',
          price: {
            actual: '3 000 000 $',
          },
          state: 'default'
        },
        {
          img: {
            jpg: 'cards/3.jpg',
            jpg2x: 'cards/3@2x.jpg',
            webp: 'cards/3.webp',
            webp2x: 'cards/3@2x.webp'
          },
          type: 'jpg',
          title: '«Сотворение Адама» Микеланджело',
          price: {
            actual: '5 000 000 $',
            old: '6 000 000 $'
          },
          state: 'inCart'
        },
        {
          img: {
            jpg: 'cards/4.jpg',
            jpg2x: 'cards/4@2x.jpg',
            webp: 'cards/4.webp',
            webp2x: 'cards/4@2x.webp'
          },
          type: 'jpg',
          title: '«Урок анатомии» Рембрандт',
          price: {
            actual: '3 000 000 $'
          },
          state: 'sold'
        }
      ],
      axiosData: {},
      errors: [],
      lsData: []
    }
  },
  methods: {
    setLsData() {
      let arr = [];
      for (let i = 0; i < this.products.length; i++) {
        arr.push(this.products[i].state);
      }
      let serialArr = JSON.stringify(arr);
      localStorage.setItem('productsState', serialArr);
    },
    getProduct(index) {
      if(this.products[index].state === 'default') {
        this.products[index].state = 'inProgress';
        this.setLsData();
        axios.get('https://jsonplaceholder.typicode.com/posts/1')
          .then(response => {
            this.axiosData = response.data;
            this.products[index].state = 'inCart';
            this.setLsData();
          })
          .catch(e => {
            this.errors.push(e);
          })
      }
      if(this.products[index].state === 'inCart') {
        this.products[index].state = 'default';
        this.setLsData();
      }
    }
  },
  mounted() {
    if (localStorage.getItem('productsState') === null) {
      this.setLsData();
    } else {
      let array = JSON.parse(localStorage.getItem('productsState'));
      console.log(array);
      for (let i = 0; i < this.products.length; i++) {
        this.products[i].state = array[i];
      }
    }
  }
}
</script>

<style lang="scss">
  @import "assets/styles/variables";

  #app {
    width: 100%;
    display: flex;
    flex-direction: column;
    min-height: 100vh;
  }

  .products {
    padding: 45px 0;
    flex-grow: 1;
  }

  .products__title {
    margin: 0 0 39px 0;
    font-size: 24px;
    color: $text-brown;
  }

  .products__list {
    list-style: none;
    margin: 0;
    padding: 0;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
  }

  .products__item {
    width: calc((100% - 96px) / 4);
    min-width: 280px;
    margin-bottom: 32px;
  }
</style>
