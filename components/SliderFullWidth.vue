<template>
  <content-section>
    <div class="placeholder">
      <img :src="require('~/assets/' + path)" :alt="alt">
    </div>
  </content-section>
</template>

<script>
import ContentSection from './ContentSection.vue'
export default {
  name: 'SliderFullWidth',
  components: { ContentSection },
  props: {
    path: {
      type: String,
      require: true,
      default: ''
    },
    alt: {
      type: String,
      default: 'Большое изображение'
    }
  }
}
</script>

<style scoped>
section{
    padding: 0;
}
.placeholder {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 300px;
  height: 35vh;
  max-height: 400px;
  overflow: hidden;
}
img {
  object-fit: contain;
  height: 100%;
}
</style>
