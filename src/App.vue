<script setup>

import { ref } from 'vue';
const header = ref('Mi Carrito de Compras');

const items = ref([
  // {id: 1, label: '3 Chocolates'},
  // {id: 2, label: '1 jugo'},
  // {id: 3, label: '4 galletas'}
]);
//agregando metodo para guardaar nuevo articulo en la lista 
const saveItem =()=> {
  items.value.push({id: items.value.length +1 , label: newItem.value})
  //limpiando el contenido de newItem
  newItem.value = "";
};
const newItem = ref('');
const newItemHighPriority = ref("false");
</script>

<template>
  <div class="header">
     <h1> <i class="material-icons shopping-cart-icon">local_mall</i> {{ header }}</h1>
    <button class="btn">Cancelar</button>
    <button class="btn btn-primary">agregar articulo</button>
  </div>
  <form v-on:submit.prevent="saveItem" class="add-item form">
    <input  v-model.trim="newItem" type="text" placeholder="Ingresar articulo 🛒"> 

<!-- Crtl + k +c comentarios  shift + alt flecha abajo y copia  -->
<!-- check boxes  -->
<label>
  <input v-model="newItemHighPriority" type="checkbox" >
  Alta Prioridad 
</label>

{{ newItemHighPriority ? "🔅" : "🍪" }}
<!-- boton  -->
<button  class="btn btn-primary">salvar articulo </button>
</form>

  <ul>
    <li v-for="{ id, label } in items" v-bind:key="id">
      🔹 {{ label }}
    </li>
  </ul>
  
<p v-if= "items.length == 0 ">🥀 lista de compras vacia 🥀</p>


</template>

<style scoped>

.shopping-cart-icon{
  font-size: 2rem;

}

</style>
