<script setup>

import { ref } from 'vue';
const header = ref('Mi Carrito de Compras');

const items = ref({
  "item1": { id: 1, label: '3 chocolates' },
  "item2": { id: 2, label: '1 jugo' },
  "item3": { id: 3, label: '3 galletas' },
});
</script>

<template>
  <h1>{{ header }}</h1>
  <ul>
    <li v-for="({ id, label }, index) in items" v-bind:key="id">
			🔹 -{{ index }}- {{ label }}
		</li>
  </ul>
  



</template>

<style scoped>

.shopping-cart-icon{
  font-size: 2rem;

}

</style>
