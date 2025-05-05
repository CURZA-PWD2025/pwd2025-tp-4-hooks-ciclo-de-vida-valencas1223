<template>
  <div class ="profesiones">
    <h2 class = "titulo">La lista de profesiones</h2>
    <ul v-if="cargado">
      <li v-for="p in listaProfesiones" :key="p.id" class ="item2">
        <strong>{{ p.nombre }}</strong>: {{ p.descripcion }}
      </li>
    </ul>
    <p class="cargando" v-else>Cargando Profesiones...</p>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'
import { profesiones } from './data/profesiones'
import type { profesion } from './interface/profesion'

const listaProfesiones = ref<profesion[]>([])

const cargado = ref(false)

onMounted(() => {
  
  //carga la lista del profesiones.ts
  setTimeout(() => {


    listaProfesiones.value = profesiones
    cargado.value = true
  }, 3000)
})
</script>

<style>
.profesiones{
  max-width: 600px;
  margin: 2rem auto;
  padding: 2rem;
  background-color: #151e50;
  border-radius: 10px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.08);
  font-family: Arial, sans-serif;
}
.titulo{
  text-align: center;
  color: #0c81f7;
  margin-bottom: 1.5rem;
}

.item2{
  background-color: #080606;
  padding: 1rem;
  margin-bottom: 1rem;
  border-left: 5px solid #007acc;
  border-radius: 5px;
  transition: background-color 0.3s;
}

.item2:hover{background-color: #56585a;}

.cargando{
  text-align: center;
  color: #666;
  font-style: italic;
}

</style>

