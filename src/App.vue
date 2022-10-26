<template>
  <input type="text" v-model="product.quantity">
  <h3>Prix du produit HT : {{productPriceHT}}</h3>
  <h3>Prix du produit TTC : {{productPriceTTC}}</h3>
</template>

<script setup lang="ts">
import { computed, watch } from 'vue';
import { reactive } from 'vue';
import { useRoute } from 'vue-router';


//function computed

const product = reactive ({
  productName: 'book',
  price: 20,
  quantity: 4,
  nbChangement: 0
})  

const productPriceHT = computed(() => { 
  return product.price * product.quantity
})

const productPriceTTC = computed(() => { 
  return product.price * product.quantity * 1.2
})

watch(()=> product.quantity,(newValue, oldValue) => {
  product.nbChangement++;
  console.log(newValue);
  console.log(oldValue);
})

</script>
