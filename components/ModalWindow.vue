<template>
  <div class="fade">
    <div class="window">
      <div class="close" @click="$emit('close-modal')" />
      <slot />
    </div>
  </div>
</template>

<script>
export default {
  name: 'ModalWindow'
}
</script>

<style scoped>
.fade {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(219, 219, 219, 0.89);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 999;
  backdrop-filter: blur(10px);
  overflow: auto;
}
.window {
  padding: 3rem;
  border-radius: 2rem;
  background: white;
  pointer-events: none;
  position: relative;
}
.close {
  position: absolute;
  top: 2rem;
  right: 2rem;
  height: 2rem;
  width: 2rem;
  z-index: 1;
  display: flex;
  justify-content: center;
  align-items: center;
  --thin: 0.3rem;
  cursor: pointer;
}
.close::after,
.close::before {
  background: grey;
  z-index: 2;
  position: absolute;
  border-radius: 0.2rem;
  transform: rotate(45deg);
}
.close::after {
  content: '';
  width: 100%;
  height: var(--thin);
}
.close::before {
  content: '';
  height: 100%;
  width: var(--thin);
}
h2 {
  padding: 0;
}
</style>
