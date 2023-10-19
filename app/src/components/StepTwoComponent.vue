<template>
  <div id="step-2" class="step" v-if="props.show">
    <h1 v-if="count === 3">Preparados</h1>
    <h1 v-if="count === 2">Listos</h1>
    <h1 v-if="count === 1">Ya</h1>
    <h1>{{ count }}</h1>
    <button @click="startCounter">si</button>
  </div>
</template>

<script setup lang="ts">
import { ref, watch } from 'vue'

const props = defineProps<{show: boolean}>()

const emit = defineEmits(['next'])
const count = ref(3)

watch(props, (newValue) => {
  console.log(props)
  if (newValue) {
    count.value = 3;
  }
})

function startCounter() {
  const intervalId = setInterval(() => {
    count.value--;
    if (count.value === 0) {
      clearInterval(intervalId);
      emit('next')
    }
  }, 1000)
}

</script>
