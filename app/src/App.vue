<script setup lang="ts">
import StepOneComponent from './components/StepOneComponent.vue'
import StepTwoComponent from './components/StepTwoComponent.vue'
import StepThreeComponent from './components/StepThreeComponent.vue'
import { onUpdated, ref } from 'vue'

const step = ref<number>(1)

function nextStep(value: number): void {
  step.value = value
}

onUpdated(() => {
  console.log(step.value)
})

</script>

<template>
  <div>
    <StepOneComponent :show="step === 1" @start="() => nextStep(2)" />
    <StepTwoComponent :show="step === 2" @next="() => nextStep(3)" />
    <StepThreeComponent :show="step === 3" @back="() => nextStep(1)" />
  </div>
</template>

