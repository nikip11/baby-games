<template>

<div class="loading">
  <IconComponent icon="loading" size="x5" />
</div>
</template>

<script setup lang="ts">
import IconComponent from './IconComponent.vue';


</script>

<style>
.loading {
  min-height: 450px;
  display: flex;
  align-items: center;
}
.loading svg {
  background-color: var(--white);
  border-radius: 50%;
  animation-name: spin;
  animation-duration: 4s;

}

@keyframes spin {
  0% {rotate: 0deg;}
  25% {rotate: 90deg;}
  50% {rotate: 180deg;}
  75% {rotate: 270deg;}
  100% {rotate: 360deg;}
}
</style>