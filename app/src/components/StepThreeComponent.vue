<template>

<div id="step-3" class="step" v-if="show">
  <button id="home-button" @click="$emit('back')">Inicio</button>
  <button id="back-button" @click="getPrev">Anterior</button>
  <div class="image" v-if="image">
    <img id="image" :src="image.imagenURL" :alt="image.name" loading="lazy" />
    <span id="image-name" class="image-name">{{ image.name }}</span>
  </div>
  <div v-else>
    loading
  </div>
  <button id="next-button" @click="getNext">Siguiente</button>
</div>

</template>

<script setup lang="ts">
import { ref } from 'vue';
import { Animal } from '../types';
import animals from '../assets/animals.json'
import { shuffleArray } from '../helpers/array.ts'

defineProps<{show: boolean}>()

const index = ref(0)

const shuffledAnimals = ref<Animal[]>(shuffleArray(animals))
const image = ref<Animal | null>(shuffledAnimals.value[1])


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
    index.value = index.value === 0 ? shuffledAnimals.value.length : index.value - 1
    image.value = shuffledAnimals.value[index.value]
  })
}

function delay(callback: () => void, time: number = 500) {
  setTimeout(() => {
    callback()
  }, time)
}


</script>

<style scoped>

#step-3 {
  flex-direction: row;
  flex-wrap: wrap;
  width: 100%;
  height: 100%;
}

#step-3 > div {
  overflow: hidden;
  max-width:fit-content;
  width: 100%;
  height: 100%;
}

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

.step  > #next-button {
  position: absolute;
  bottom: 20px;
  right: 20px;
}

.step > #back-button {
  position: absolute;
  bottom: 20px;
  left: 20px;
}
.step > #home-button {
  position: absolute;
  top: 20px;
  left: 20px;
}
</style>
