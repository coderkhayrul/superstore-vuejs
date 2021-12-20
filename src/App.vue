<template>
  <div id="app">
    <!-- Navbar Component Start -->
  <navbar></navbar>
  <!-- Navbar Component End -->
    <div class="container mt-3">
      <div class="row">
      <div class="col-sm-9">
        <!-- Inventory Component Start -->
        <inventory @newItemAdded="addCartItem" :items = "items" ></inventory>
        <!-- Inventory Component End -->
      </div>
      <div class="col-sm-3">
        <!-- Cart Component Start -->
        <cart @itemRemove="itemRemove" :items = "cart" ></cart>
        <!-- Cart Component End -->
      </div>
    </div>
    </div>
  </div>
</template>

<script>
import Navbar from './components/Navbar.vue'
import Inventory from './components/Inventory.vue'
import Cart from './components/Cart.vue'
import data from './data.js'
  export default {
    components: {
      Navbar,
      Cart,
      Inventory
    },
    data() {
      return {
        items:[],

        cart:[],
      }
    },
    mounted(){
      this.items = data
    },
    methods:{
      addCartItem(item){
        this.cart.push(item);
      },
      itemRemove(index){
        this.cart.splice(index,1);
      }
    }
  }

</script>

<style>

</style>
