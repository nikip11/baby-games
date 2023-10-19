<template>
  <div class="image" v-if="image">
      <img id="image" :src="image.imagenURL" :alt="image.name" loading="lazy" />
      <span id="image-name" class="image-name">{{ image.name }}</span>
    </div>
    <div v-else>
      loading
    </div>
</template>

<script setup lang="ts">
import { Animal } from '../../types';

defineProps<{image: Animal | null}>()

</script>