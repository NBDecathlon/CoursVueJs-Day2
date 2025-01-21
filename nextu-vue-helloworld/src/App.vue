<template>
  <div id="app">
    <product-list :products="products" />
  </div>
</template>

<script>
import ProductList from './components/ProductList.vue';
import AsideView from './components/layouts/AsideView.vue'
import HeaderView from './components/layouts/HeaderView.vue'
import NavView from './components/layouts/NavView.vue'
import HomeProjectView from './views/HomeProjectView.vue'

export default {
  name: 'App',
  components: {
    ProductList,
  },
  data() {
    return {
      products: [
        { id: 1, label: 'Carotte', description: 'De belles carottes', qte: 10 },
        { id: 2, label: 'Pomme', description: 'Des pommes vertes', qte: 0 },
        { id: 3, label: 'Tomate', description: 'Tomates rouges', qte: 5 },
      ],
    };
  },
};
</script>

<style>
</style>
