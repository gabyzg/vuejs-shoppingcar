<script setup>

import { ref } from 'vue';
const header = ref('Mi Carrito de Compras');

const items = ref([
  // ctr + k + u para descomentar
  {id: 1, label: '3 Chocolates', purchased: true, highPriority: true} ,
  {id: 2, label: '1 jugo', purchased: false,  highPriority: true},
  {id: 3, label: '4 galletas', purchased: true,  highPriority: false}
]);
//funcion que alterna el estado de compredo de un item 
const togglePurchased = (item) => {
  //invertir la propiedad purchased
  item.purchased = !item.purchased;
 }

//agregando metodo para guardaar nuevo articulo en la lista 
const saveItem =() => {
  items.value.push({id: items.value.length +1 , label: newItem.value})
  //limpiando el contenido de newItem
  newItem.value = "";
};
const newItem = ref('');
const newItemHighPriority = ref(false);
const editing = ref(false);

const doEdit = (edit) => {
  //altero la variable editing
  editing.value = edit;
  //limpio el input de texto 
  newItem.value = "";
};

 
</script>

<template>
  <div class="header">
     <h1> <i class="material-icons shopping-cart-icon">local_mall</i> {{ header }}</h1>
     <button v-if="!editing" @click="doEdit(true)" class="btn btn-primary">agregar articulo</button>
    <button  v-else   @click="doEdit(false)" class="btn">Cancelar</button>
  
  </div>
  <form v-if="editing" v-on:submit.prevent="saveItem" class="add-item form" >
    <input  v-model.trim="newItem" type="text" placeholder="Ingresar articulo 🛒"> 

<!-- Crtl + k +c comentarios  shift + alt flecha abajo y copia  -->
<!-- check boxes  -->
<label>
  <input v-model="newItemHighPriority" type="checkbox" >
  Alta Prioridad 
</label>

{{ newItemHighPriority ? "🔅" : "🍪" }}
<!-- boton  -->
<button :disabled="newItem.length === 0" class="btn btn-primary">salvar articulo </button>
</form>

  <ul>
    <li
     v-for="({ id, label, purchased, highPriority }, index ) in items" v-bind:key="id"
     :class="{ strikeout : purchased,  priority : highPriority}"
     @click="togglePurchased(items[index])"
     >
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
