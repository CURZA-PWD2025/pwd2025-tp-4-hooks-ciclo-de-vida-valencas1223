<template>
  
  <div v-if="mensaje" class="alerta">{{ mensaje }}</div>
</template>

<script setup lang="ts">

defineProps<{ mensaje: string }>()
</script>

<style scoped>
.alerta {
  padding: 1rem;
  background-color: #fdd;
  color: #900;
  border: 1px solid #900;
  border-radius: 5px;
  margin-bottom: 1rem;
}
</style>

  