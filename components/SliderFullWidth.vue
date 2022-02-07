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
  margin-top: var(--container-padding);
  display: flex;
  /* justify-content: center; */
  /* align-items: center; */
  /* min-height: 300px; */
  max-height: 50rem;
  width: 100%;
  overflow: hidden;
}
.placeholder img {
  max-width: 100%;
  max-height: 100%;
  width: 100%;
  object-fit: contain;
}
</style>
