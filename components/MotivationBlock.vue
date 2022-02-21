<template>
  <content-section class="motivation">
    <h2>{{ data.title }}</h2>
    <div class="content">
      <icon-text
        v-for="(item, i) in data.content"
        :key="i"
        :icon="'motivation/' + item.icon"
        :description="item.description"
      />
    </div>
  </content-section>
</template>

<script>
import IconText from './Cards/IconText.vue'
import ContentSection from './ContentSection.vue'
export default {
  name: 'MotivationBlock',
  components: { ContentSection, IconText },
  props: {
    data: {
      type: Object,
      default: null
    }
  }
}
</script>

<style scoped>
.motivation {
  --padding: 0;
}
.content {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-gap: 6rem 10rem;
  padding: 0 var(--padding);
}
h2 {
  padding: 0 var(--padding) 3rem;
}
</style>
