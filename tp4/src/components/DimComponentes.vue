<template>
    <div>
      <h2>Dimensión del componente</h2>
      <p>width: {{ width }}px</p>
      <p>height: {{ height }}px</p>
    </div>
  </template>
  
  <script setup lang="ts">
  import { ref, onMounted, onUnmounted } from 'vue'
  
  const width = ref(window.innerWidth)

  const height = ref(window.innerHeight)
  
  const actualizarDimensiones = () => {

    width.value = window.innerWidth

    height.value = window.innerHeight
  }
  
  onMounted(() => {

    window.addEventListener('resize', actualizarDimensiones)

  })
  
  onUnmounted(() => {

    window.removeEventListener('resize', actualizarDimensiones)

  })
  </script>

  <style> 
p{
  color: black;
}
</style>
  
  