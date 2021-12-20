<template>
  <ul class="list-group">
    <li class="list-group-item">
      <span class="item-name">Name</span>
      <span class="item-price float-right">Price</span>
    </li>
    <hr>
    <li v-for="(item, index) in items" :key="index" class="list-group-item">
      <span class="item-name">{{ item.title }}</span>
      <button class="btn btn-danger btn-sm" @click="removeItem(index)">X</button>
      <span class="item-price float-right">${{ item.price }}</span>
    </li>
    <hr>
    <li class="list-group-item">
      <span class="item-name"><strong>Total</strong></span>
      <span class="item-price float-right">${{ totalPrice }}</span>
    </li>

  </ul>
</template>
<script>
  export default {
    props:['items'],
    computed:{
      totalPrice() {
        var total = 0;
        this.items.forEach(item => {
          total += parseFloat(item.price);
        })
        return total;
      }
    },
    methods: {
      removeItem(index) {
        this.$emit('itemRemove', index);
      }
    }
  }

</script>
<style>

</style>
