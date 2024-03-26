<template>
    <div class="d-flex flex-wrap align-item-center">
          <div v-for="item in products" :key="item.id" class="card col-2 my-1 mx-1">
            <a href="#" class="card-body text-dark text-decoration-none">
              <img :src="item.image" referrerpolicy="no-referrer" class="card-img-top mb-2 " style="height: 150px; object-fit: scale-down;" alt="...">
              <p href="#" class="card-title text-truncate" >{{ item.title }}</p>
              <h5 class="card-text mt-auto">
                <price :value="Number(item.price)"></price>
              </h5>
            </a>
            <button type="button" class="btn btn-success mb-sm-2" @click="$emit('addCart',item)">
              <span class="material-symbols-outlined" style="vertical-align: middle;"></span>
              <span style="vertical-align: middle;">Buy</span>
            </button>
          </div>
        </div>
</template>
<script>
import price from './price.vue'

export default{
    name: 'product-list',
    components : {
        price
    },
    
    props: ['products'] 
}
</script>