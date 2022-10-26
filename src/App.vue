<template>
  <h1 :class="maClasse">Bonjour {{state.user2.name2}}</h1>
  <input :type="inputType">
  <h2>Count : {{state.count}}</h2>
  <button @click="state.count++">add</button>
  <h3>Prix du produit HT : {{productPriceHT}}</h3>
  <h3>Prix du produit TTC : {{productPriceTTC}}</h3>
</template>

<script setup lang="ts">
import { computed } from 'vue';
import { reactive } from 'vue';
import { useRoute } from 'vue-router';


const name = 'Maxime';  
const maClasse = 'title';
const inputType = 'number'; 

const user2 = {
  name2: 'Tintin',
  age2: 23
}

const state = reactive({
  user2,
  count:0
});

setTimeout(() => {
  state.user2.name2 = 'Maxime';
},3000)

//typescript

interface User {
  name: string;
  age: number | string;
}

let user: User;

function creatUser(name: string): User{
  return{
    name ,
    age: 22
  }
}

user = creatUser('Maxime');

//function computed

const product = reactive ({
  productName: 'book',
  price: 20,
  quantity: 4
})  

const productPriceHT = computed(() => { 
  return product.price * product.quantity
})

const productPriceTTC = computed(() => { 
  return product.price * product.quantity * 1.2
})

</script>

<style>
.title{
  color: red;
}

</style>