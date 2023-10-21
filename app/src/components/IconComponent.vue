<template>
  <svg
  xmlns="http://www.w3.org/2000/svg"
  height="24"
  viewBox="0 -960 960 960"
  :class="size"
  width="24">
    <path v-if="icon === 'home'" d="M240-200h120v-240h240v240h120v-360L480-740 240-560v360Zm-80 80v-480l320-240 320 240v480H520v-240h-80v240H160Zm320-350Z"/>
    <path v-if="icon === 'arrowLeft'" d="M560-280 360-480l200-200v400Z" />
    <path v-if="icon === 'arrowRight'" d="M400-280v-400l200 200-200 200Z"/>
    <path v-if="icon === 'loading'" d="M482-160q-134 0-228-93t-94-227v-7l-64 64-56-56 160-160 160 160-56 56-64-64v7q0 100 70.5 170T482-240q26 0 51-6t49-18l60 60q-38 22-78 33t-82 11Zm278-161L600-481l56-56 64 64v-7q0-100-70.5-170T478-720q-26 0-51 6t-49 18l-60-60q38-22 78-33t82-11q134 0 228 93t94 227v7l64-64 56 56-160 160Z"/>
  </svg>
</template>
<script setup lang="ts">
type Props = {
  icon: 'home' | 'arrowLeft' | 'arrowRight' | 'loading'
  size: 'x2' | 'x3' | 'x4' | 'x5'
}

defineProps<Props>()

</script>

<style scoped>
.icon {
  font-size: 5em;
}
.x2 {transform: scale(2);}
.x3 {transform: scale(3);}
.x4 {transform: scale(4);}
.x5 {transform: scale(5);}
</style>