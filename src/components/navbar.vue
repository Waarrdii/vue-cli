<template>
    <nav class="navbar navbar-expand-lg navbar-light bg-light sticky-top">
          <span class="material-symbols-outlined">storefront</span>
          <a class="navbar-brand" href="#">Toko Kita</a>
          <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
          </button>
        
          <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <form class="form-inline ml-auto">
              <input class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search">
              <button class="btn btn-outline-success my-2 my-sm-0" type="submit">Search</button>
            </form>
            <ul class="navbar-nav my-2 my-lg-0">
              <li class=" dropdown nav-item position-relative">
                <a class="nav-link" href="#"  role="button" data-toggle="dropdown" aria-expanded="true" >
                <span class="material-symbols-outlined">shopping_cart</span>
                <span class="badge badge-pill badge-danger position-absolute" style="top: -3px; right: 0;" v-if="cart.length > 0"><span>{{ totalQty }}</span></span>
                </a>
                <ul v-show="cart.length > 0" class="dropdown-menu dropdown-menu-right">
                  <li v-for="(item, index) in cart" class="d-flex flex-row justify-content-between mb-3">
                    <img :src="item.product.image" style="height: 40px; width: 40px; object-fit: scale-down;" alt="...">
                    <div class="text-truncate mx-2" style="width: 150px;">{{ item.product.title }}</div>
                    <div class="d-flex flex-row justify-content-between px-sm-2" style="width: 110px;"><span>{{ item.qty }} x </span><span class="text-right ">{{ item.product.price | formatCurrency}}</span></div>
                    <div class="text-right px-sm-2" style="width: 100px;">{{ item.total | formatCurrency}}</div>
                    <a href="#" class="badge badge-danger text-white" @click="$emit('deleteItem',index)">-</a>
                  </li>
                  <b>Total Belanja : {{calculateItem | formatCurrency}}</b>
                </ul>
              </li>
              <li class="nav-item">
                <a class="nav-link" href="#">
                  <span class="material-symbols-outlined">notifications</span>
                </a>
              </li>
              <li class="nav-item dropdown">
                <a class="nav-link dropdown-toggle" href="#" role="button" data-toggle="dropdown" aria-expanded="false">
                  <span class="material-symbols-outlined">person</span>
                </a>
                <div class="dropdown-menu dropdown-menu-right">
                  <a class="dropdown-item" href="#">Profile</a>
                  <a class="dropdown-item" href="#">Setting</a>
                  <div class="dropdown-divider"></div>
                  <a class="dropdown-item" href="#">Log Out</a>
                </div>
              </li>
            </ul>
            
          </div>
        </nav>

</template>
<script>
export default {
    name: "navbar"
    
}
</script>