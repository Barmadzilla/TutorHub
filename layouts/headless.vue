<template>
  <div>
    <nuxt />
  </div>
</template>

<script>
export default {
  name: 'LayoutHeadless',
  layout (context) {
    return 'headless'
  }
}
</script>

<style>
.page-enter-active,
.page-leave-active {
  transition: opacity 0.3s;
}
.page-enter,
.page-leave-to {
  opacity: 0;
}

.layout-enter-active,
.layout-leave-active {
  transition: opacity 0.3s;
}
.layout-enter,
.layout-leave-to {
  opacity: 0;
}
</style>
