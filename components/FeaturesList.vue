<template>
  <content-section>
    <h2>
      {{ data.title }}
    </h2>
    <div class="content">
      <feature-card
        v-for="(item, i) in data.content"
        :key="i"
        :photo="item.photo"
        :description="item.description"
      />
    </div>
  </content-section>
</template>

<script>
import FeatureCard from './Cards/FeatureCard.vue'
import ContentSection from './ContentSection.vue'
export default {
  name: 'FeaturesList',
  components: { ContentSection, FeatureCard },
  props: {
    data: {
      type: Object,
      default: null
    }
  }
}
</script>

<style scoped>
h2 {
  padding-bottom: 5rem;
}
.content{
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  place-items: center;
  grid-gap: 5rem;
}
</style>
