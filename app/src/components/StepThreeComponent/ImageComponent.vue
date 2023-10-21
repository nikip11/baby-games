<template>
  <div class="image" v-if="image">
      <span class="image-name">{{ image.name }}</span>
      <img :src="image.imagenURL" :alt="image.name" loading="lazy" />
  </div>
  <LoadingComponent v-else/>
</template>

<script setup lang="ts">
import { Animal } from '@/types'
import LoadingComponent from '@/components/LoadingComponent.vue'
defineProps<{image: Animal | null}>()
</script>

<style>
.image {
  position: relative;
  display: flex;
  flex-direction: column;
}
.image .image-name {
  color: #ffffff;
  display: block;
  margin: 10px;
  font-family: var(--open-sans);
  font-size: 5em;
  text-transform: uppercase;
}
.image img {
  max-width: 100%;
  max-height: 600px;
  width: 550px;
  background-color: var(--primary);
  border-radius: 20px;
  border: 30px solid var(--primary);
}

@media only screen 
  and (min-device-width: 428px)
  and (-webkit-device-pixel-ratio: 3)
  and (orientation: portrait) {
  
  .image .image-name {
    font-size: 3em;
  }
  .image img {
    width: calc(100% - 20px);
    border: 10px solid var(--primary);
  }
}

@media only screen 
    and (min-device-width: 428px)
    and (-webkit-device-pixel-ratio: 3)
    and (orientation: landscape) {
  .image .image-name {
    font-size: 2em;
    justify-self: flex-end;
  }
  .image img {
    justify-self: flex-start;
    width: 300px;
    border: 10px solid var(--primary);
  }
}

</style>