<script setup>

import { ref } from 'vue';
const header = ref('Mi Carrito de Compras');

const items = ref([
  {id: 1, label: '3 Chocolates'},
  {id: 2, label: '1 jugo'},
  {id: 3, label: '4 galletas'}
]);
</script>

<template>
  <h1> <i class="material-icons shopping-cart-icon">local_mall</i> {{ header }}</h1>
  <ul>
    <li v-for="{ id, label } in items" v-bind:key="id">
      🔹 {{ label }}
    </li>
  </ul>
  



</template>

<style scoped>

.shopping-cart-icon{
  font-size: 2rem;

}

</style>
