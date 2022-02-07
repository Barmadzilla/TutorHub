<template>
  <content-section>
    <h2>{{ data.title }}</h2>
    <div class="scroll">
      <div class="roadmap">
        <card-path
          v-for="(step, i) in data.content"
          :key="i"
          :data="step"
          :number="i + 1"
        />
      </div>
    </div>
  </content-section>
</template>

<script>
import CardPath from './Cards/CardPath.vue'
import ContentSection from './ContentSection.vue'
export default {
  name: 'RoadMap',
  components: { ContentSection, CardPath },
  props: {
    data: {
      type: Object,
      default: null
    }
  }
}
</script>

<style scoped>
.scroll {
  overflow: auto;
  padding-bottom: 1em;
}
.roadmap {
  padding-top: var(--section-padding);
  display: flex;
  gap: 3em;
  width: max-content;
}
</style>
