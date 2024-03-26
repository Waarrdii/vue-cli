<template>
  <div id="app">
    <div class="container-fluid">
      <product-list :products="products" @addCart="addCart()"></product-list>
    </div>
    
  </div>
</template>

<script>
import productList from './components/product-list.vue';
import axios from 'axios';

export default {
  data() {
    return {
      products: [],
      cart: []
    };
  },
  mounted() {
    axios.get(`https://fakestoreapi.com/products`)
      .then(response => {
        this.products = response.data;
      })
      .catch(error => {
        console.error('Kesalahan saat mengambil produk:', error);
      });
  },
  methods:{
      addCart: function (product) {
          // this.cart.push(product)
          const productIndex = this.cart.findIndex(item => item.product.id === product.id);
          let total = product.price;
          if (productIndex === -1) {
            // Produk baru
            this.cart.push({ product, qty: 1, total });
           
          } else {
            // Produk sudah ada, tingkatkan qty
            this.cart[productIndex].qty++;
            total = total * this.cart[productIndex].qty;
            this.cart[productIndex].total = total;
            // console.log(product.price,this.cart[productIndex].qty,total)

          }
          
        }
    },
  components: {
    productList
  },

}
</script>
