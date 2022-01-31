<template>
  <nuxt-link :to="to" class="btn">
    {{ title }}
  </nuxt-link>
</template>

<script>
export default {
  name: 'ButtonMain',
  props: {
    to: {
      type: String,
      default: '#'
    },
    title: {
      type: String,
      default: 'Press Me'
    }
  }
}
</script>
