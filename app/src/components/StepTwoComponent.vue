<template>
  <div id="step-2" class="step" v-if="props.show">
    <div v-if="!showPrepared">
      <h1>¿Estás preparado?</h1>
      <button @click="startCounter">si</button>
      <button @click="$emit('back')">no</button>
    </div>
    <div v-else>
      <h1 v-if="count === 3">Preparados</h1>
      <h1 v-if="count === 2">Listos</h1>
      <h1 v-if="count === 1">Ya</h1>
      <h1>{{ count }}</h1>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, watch } from 'vue'

const props = defineProps<{ show: boolean }>()

const showPrepared = ref(false)

const emit = defineEmits(['next', 'back'])
const count = ref(3)

watch(props, (newValue) => {
  if (newValue) {
    count.value = 3;
    showPrepared.value = false
  }
})

function startCounter() {
  showPrepared.value = true
  const intervalId = setInterval(() => {
    count.value--;
    if (count.value === 0) {
      clearInterval(intervalId);
      emit('next')
    }
  }, 1000)
}

</script>
<style scoped>
button {
  margin-right: 20px;
}
</style>