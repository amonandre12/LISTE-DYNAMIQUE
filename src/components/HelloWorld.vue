<script setup>
// Fonction the list 
import { ref } from 'vue'
const items = ref([]) ;
const newTask = ref('') ;
const maxItems = 5;

// Fonction pour ajouter de nouvelle tache

const addTask = () =>{
if(newTask.value.trim() && items.value.length < maxItems) {
items.value.push(newTask.value.trim()); 
newTask.value ='' ;
}
} ;

// fonction the delete the task 

const deleteTask = (index) => {
  items.value.splice(index, 1) ;
}

</script>

<template>
  <div class="input-classe">
  <input v-model="newTask" placeholder="Add the new task">
  <button @click="addTask" class="btn">Ajouter</button>
  <p v-if="items.length >= maxItems"> Vous ne pouvez ajouter que 5 elements </p>
  </div>
  <ul>
    <li v-for="(item, index) in items" :key="index">
      {{ item }}
      <button @click="deleteTask(index)"> Supprimer</button>
    </li>
  </ul>
</template>

<style scoped>

.input-classe {
  text-align: center;
  margin-top: 10%;
}
.btn, input {
  padding: 15px;
}

.btn,button{
  cursor: pointer;
}
</style>
