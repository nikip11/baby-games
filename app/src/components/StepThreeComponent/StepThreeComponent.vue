<template>

  <div id="step-3" class="step" v-if="show">
    <ImageComponent :image="image" />
    <div class="buttons">
      <button @click="getPrev"> <IconComponent icon="arrowLeft" size="x3"/> Prev</button>
      <button @click="$emit('back')"><IconComponent icon="home" size="x2"/></button>
      <button @click="getNext">Next <IconComponent icon="arrowRight" size="x3"/></button>
    </div>
  </div>
  
</template>
  
<script setup lang="ts">
import { ref } from 'vue';
import { Animal } from '@/types';
import animals from '@/assets/animals.json'
import { shuffleArray } from '@/helpers/array.ts'
import ImageComponent from './ImageComponent.vue';
import IconComponent from '@/components/IconComponent.vue'

defineProps<{show: boolean}>()

const index = ref(0)

const shuffledAnimals = ref<Animal[]>(shuffleArray(animals))
const image = ref<Animal | null>(shuffledAnimals.value[index.value])

function getNext() {
  image.value  = null
  delay(() => {
    index.value = shuffledAnimals.value.length === index.value ? 0 : index.value + 1
    image.value = shuffledAnimals.value[index.value]
  })
}

function getPrev() {
  image.value  = null
  delay(() => {
    index.value = index.value === 0 ? shuffledAnimals.value.length - 1 : index.value - 1
    image.value = shuffledAnimals.value[index.value]
  })
}

function delay(callback: () => void, time: number = 750) {
  setTimeout(() => {
    callback()
  }, time)
}

</script>

<style scoped>
#step-3 {
  flex-direction: column;
  flex-wrap: wrap;
  width: 100%;
  height: 100%;
}

.step .buttons {
  /* width: 100%; */
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 30px;
  margin: 30px 0px;
}

@media only screen 
  and (min-device-width: 428px)
  and (-webkit-device-pixel-ratio: 3)
  and (orientation: portrait) {
  .step .buttons {
    gap: 10px;
  }
}
@media only screen 
  and (min-device-width: 428px)
  and (-webkit-device-pixel-ratio: 3)
  and (orientation: landscape) {
  .step .buttons {
    margin: 10px 0px;
  }
}
</style>
  