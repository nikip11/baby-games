<script setup lang="ts">
import StepOneComponent from './components/StepOneComponent.vue'
import StepTwoComponent from './components/StepTwoComponent.vue'
import StepThreeComponent from './components/StepThreeComponent/StepThreeComponent.vue'
import { ref } from 'vue'

const step = ref<number>(1)

function nextStep(value: number): void {
  step.value = value
}

</script>

<template>
  <div>
    <StepOneComponent :show="step === 1" @start="() => nextStep(2)" />
    <StepTwoComponent :show="step === 2" @next="() => nextStep(3)" />
    <StepThreeComponent :show="step === 3" @back="() => nextStep(1)" />
  </div>
</template>

<style>
#step-3 > div > img {
    max-width: 100%;
    height: auto;
    max-height: 350px;
    object-fit: cover;
    object-position: center center;
    min-width: 560px;
    border: solid 2px #333;
  }
  #step-3 > div > .image-name {
    background-color: rgba(255, 255, 255, 0.95);
    border-radius: 10px;
    width: auto;
    padding: 7px 25px;
    min-width: 180px;
    margin-top: -15px;
    border: 1px solid #333;
    font-weight: bold;
    font-size: 1.5em;
    color: var(--black);
    text-transform: uppercase;
    position: absolute;
    bottom: 20px;
    left: calc(50% - 115px);
}
</style>