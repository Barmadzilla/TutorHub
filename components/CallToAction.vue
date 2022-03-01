<template>
  <content-section color="theme" type="action">
    <div class="columns">
      <p><slot /></p>
      <a v-if="to.external" :href="to.link" class="btn">
        {{ to.name }}
      </a>
      <nuxt-link v-if="!to.external" :to="to.link" class="btn">
        {{ to.name }}
      </nuxt-link>
    </div>
  </content-section>
</template>

<script>
import ContentSection from './ContentSection.vue'
export default {
  components: { ContentSection },
  props: {
    to: {
      type: Object,
      default: null
    }
  }
}
</script>

<style scoped>
.columns{
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 7rem;
}
p{
  margin-bottom: 0;
}
a{
  white-space: nowrap;
}
@media (max-width: 750px){
  .columns {
    flex-direction: column;
    text-align: center;
    gap: 3em;
    justify-items: center;
  }
}
</style>
