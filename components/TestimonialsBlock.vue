<template>
  <content-section>
    <h2>{{ data.title }}</h2>
    <div class="content">
      <testimonial-card
        v-for="(item, i) in data.content"
        :key="i"
        :name="item.name"
        :text="item.text"
      />
    </div>
  </content-section>
</template>

<script>
import TestimonialCard from './Cards/TestimonialCard.vue'
import ContentSection from './ContentSection.vue'
export default {
  name: 'TestimonialsBlock',
  components: { ContentSection, TestimonialCard },
  props: {
    data: {
      type: Object,
      default: null
    }
  }
}
</script>

<style scoped>
.content {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 3rem;
}
@media (max-width:750px) {
  .content {
  grid-template-columns: repeat(1, 1fr);
}
}
</style>
