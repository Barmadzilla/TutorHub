<template>
  <content-section>
    <div v-if="!position">
      <h2>{{ data.title }}</h2>
      <p v-for="(p, i) in data.content" :key="i">
        {{ p }}
      </p>
    </div>
    <div v-else :class="['content', position]">
      <div v-if="position === 'right'" />
      <div class="first">
        <h2>{{ data.title }}</h2>
        <p v-for="(p, i) in data.content" :key="i" v-html="p" />
      </div>
      <div v-if="position === 'left'" />
    </div>
  </content-section>
</template>

<script>
import ContentSection from './ContentSection.vue'

export default {
  name: 'InfoBlock',
  components: { ContentSection },
  props: {
    data: {
      type: Object,
      default: null
    },
    position: {
      type: String,
      default: null
    }
  }
}
</script>
<style scoped>
.content {
  display: grid;
  grid-template-columns: 1fr;
}
.content.right {
  grid-template-columns: 2fr 5fr;
}
.content.left {
  grid-template-columns: 5fr 2fr;
}
.content p {
  text-align: justify;
  text-justify: distribute
}
@media (max-width: 900px) {
  .content.right,
  .content.left {
  grid-template-columns: 1fr;
}

}
@media (max-width: 480px) {
}
</style>
