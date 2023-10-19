<template>
  <div id="step-1" class="step" v-if="show">
    <h1>¡Juego de Charadas para Niños!</h1>
    <button @click="$emit('start')">comenzamos</button>
  </div>
</template>
<script setup lang="ts">
defineProps<{show: boolean}>()
</script>
<style scoped>

</style>
