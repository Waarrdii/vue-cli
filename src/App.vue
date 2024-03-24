<template>
  <div id="app">
    <div class="container-fluid">
      <product-list :products="products"></product-list>
    </div>
    
  </div>
</template>

<script>
import productList from './components/product-list.vue';
import axios from 'axios';

export default {
  name: 'App',
  data : function(){
    return{
      products : []
    }
  },
  components: {
    productList
  },
  mounted() {
        // Fetch data produk dari WooCommerce API
        axios.get(`https://fakestoreapi.com/products`)
          .then(response => {
            // Simpan data produk dalam state
            this.products = response.data
            // console.log(this.products)
          })
      },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>./components/product-list.vue
