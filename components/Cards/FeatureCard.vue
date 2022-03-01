<template>
  <div class="feature">
    <img :src="require('~/assets/photos/features/' + photo)" alt="Feature image">
    <p>{{ description }}</p>
  </div>
</template>

<script>
export default {
  name: 'FeatureCard',
  props: {
    photo: { type: String, default: 'photo_01.jpg' },
    description: { type: String, default: null }
  }
}
</script>

<style scoped>
.feature {
  display: flex;
  justify-content: flex-start;
  flex-direction: column;
  align-items: center;
  max-width: 40rem;
  gap: 2rem;
}
p {
  text-align: center;
}
img {
  width: 10rem;
  height: 10rem;
}
</style>
