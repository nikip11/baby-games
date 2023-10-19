<template>
  <div id="step-2" class="step" v-if="show">
    <h1 v-if="count === 3">Preparados</h1>
    <h1 v-if="count === 2">Listos</h1>
    <h1 v-if="count === 1">Ya</h1>
    <h1>{{ count }}</h1>
  </div>
</template>

<script setup lang="ts">
import { onActivated, onMounted, onRenderTracked, onUpdated, ref, toRefs, watch } from 'vue'

const props = defineProps<{show: boolean}>()
const { show } = toRefs({show: props.show})

const emit = defineEmits(['next'])
const count = ref(3)

watch(show, (newValue) => {
  if (newValue) {
    count.value = 3;
    startCounter();
  }
})

onMounted(() => {
  console.log('onMounted')
  startCounter()
})

onUpdated(() => {
  console.log('onUpdated')
  // startCounter()
})
onRenderTracked(() => {
  console.log('onRenderTracked')
  // startCounter()
})
onActivated(() => {
  console.log('onActivated')
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
