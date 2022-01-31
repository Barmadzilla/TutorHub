<template>
  <content-section :type="'header'">
    <navigation />
  </content-section>
</template>

<script>
import ContentSection from './ContentSection.vue'
import Navigation from './Navigation.vue'
export default {
  name: 'HeaderBlock',
  components: { ContentSection, Navigation }
}
</script>

<style></style>
