<template>
  <div class="placeholder">
    <img :src="require('~/assets/icons/inclu_icon_' + icon + '.png')">
  </div>
</template>

<script>
export default {
  name: 'CardIcon',
  props: {
    icon: {
      type: String,
      default: '0'
    }
  }
}
</script>
<style scoped>
.placeholder {
  background: white;
  border-radius: 2rem;
  display: flex;
  justify-content: center;
  align-items: center;
  border: solid .3em var(--theme-color);
  padding: 2em;
  width: 15em;
  height: 10em;
}
img{
  object-fit: scale-down;
  /* height: 100%; */
  max-height: 7.5em;
  max-width: 7.5em;
}
</style>
