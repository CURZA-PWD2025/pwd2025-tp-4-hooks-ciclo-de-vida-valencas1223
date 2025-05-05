<template>
  <div  class = "componente">
    <label  class = "etiqueta" for="selector">Seleccionar componente:</label>
    <select id="selector" v-model="seleccionDecomponentes" class="selector">
      <option value="Lista">Lista</option>
      <option value="Tareas">Tareas</option>
      <option value="Dimension">Dimensión</option>
    </select>
    <hr class="separador" />
    <component :is="componentes[seleccionDecomponentes]" />
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import Lista from "./components/Lista.vue"
import Tareas from "./components/Tareas.vue"
import Dimension from "./components/DimComponentes.vue"

//variables que guardan el componente que el usuario va a seleccionar
const seleccionDecomponentes = ref<'Lista' | 'Tareas' | 'Dimension'>('Lista')

const componentes = {
  Lista,
  Tareas,
  Dimension
} as const
</script>

<style>
.componente{
  max-width: 700px;
  margin: 2rem auto;
  padding: 2rem;
  background-color: #f4faff;
  border-radius: 12px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.08);
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}
.etiqueta {
  font-size: 1.1rem;
  font-weight: 600;
  display: block;
  margin-bottom: 0.5rem;
  color: #004080;
}

.selector {
  width: 100%;
  padding: 0.6rem;
  font-size: 1rem;
  border-radius: 6px;
  border: 1px solid #000000;
  margin-bottom: 1.5rem;
  background-color: #1f1111;
  transition: border 0.3s;
}

.selector:focus {
  outline: none;
  border-color: #007acc;
}

.separador {
  margin: 1.5rem 0;
  border: none;
  border-top: 2px solid #cce6ff;
}



</style>



