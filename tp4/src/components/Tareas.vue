<template>
  <div  class = "tarea">
    <Alerta :mensaje="mensaje" />

    <input
      type="text"

      v-model="nuevaTarea"

      @keyup.enter="agregarTarea"
      
      placeholder="Escribi la nueva tarea"
    />

    <ul class = "lista">
      <li
      class="item"
        v-for="(tarea, index) in tareas"

        :key="index"

        :style="{ color: index < tareasOriginales ? 'blue' : 'black' }"

      >
        {{ tarea }}

      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">

import { ref, onBeforeUpdate, onUpdated } from "vue"
import Alerta from "./Alerta.vue"

const tareas = ref <string[]> (["tarea 1", "tarea 2"])

const tareasOriginales = tareas.value.length

const nuevaTarea = ref("")

const mensaje = ref("")

onBeforeUpdate(() => {

  console.log('Lista aún no modificada')

})

onUpdated(() => {

  console.log('Lista modificada')

})

const agregarTarea = () => {

  const tarea = nuevaTarea.value.trim()

  if(tarea){
    tareas.value.push(tarea)
    mensaje.value = "la tareas se agrego bien"
    
  }else{
    mensaje.value = "no hay mensaje disponible"
  }
    setTimeout (()=> (mensaje.value= "") ,  3000)
  

  nuevaTarea.value = ""
}


</script>

<style>
.tarea{
  padding: 2rem;
  max-width: 600px;
  margin: auto;
  background-color: #f7f9fc;
  border: 1px solid #ddd;
  border-radius: 8px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.05);
  font-family: 'Segoe UI', sans-serif;
}
.lista{
 list-style: none;
  padding: 0; 
}


h2{
  color: #333;
  margin-bottom: 1.5rem;
  text-align: center;
}

.item{
  background-color: #ffffff;
  border: 1px solid #ddd;
  border-radius: 6px;
  padding: 0.8rem 1rem;
  margin-bottom: 0.8rem;
  transition: transform 0.2s ease;
}
.item:hover {
  transform: translateX(5px);
  background-color: #eef6ff;
}
</style>

{}
