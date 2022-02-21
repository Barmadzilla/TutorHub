<template>
  <div class="motivation">
    <img :src="require('~/assets/icons/' + icon)" alt="Motivation Icon">
    <p>{{ description }}</p>
  </div>
</template>

<script>
export default {
  name: 'IconText',
  props: {
    icon: {
      type: String,
      default: ''
    },
    description: {
      type: String,
      default: ''
    }
  }
}
</script>

<style scoped>
.motivation {
  display: flex;
  justify-content: flex-start;
  align-items: flex-start;
  gap: 2rem;
}

</style>
