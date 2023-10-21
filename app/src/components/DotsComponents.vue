<template>

<div class="dots">
      <span></span>
      <span></span>
      <span></span>
      <span></span>
      <span></span>
      <span></span>
    </div>
</template>
<style>

.dots { 
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
}
.dots span {
  width: 30px;
  height: 30px;
  background-color: var(--primary);
  border-radius: 50%;
  display: block;
  margin: 40px 20px;
  -webkit-box-shadow: 1px 1px 0px 2px var(--secundary);
  box-shadow: 1px 1px 0px 2px var(--secundary);
}
</style>