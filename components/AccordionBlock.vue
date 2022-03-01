<template>
  <content-section color="theme">
    <h2 v-if="data.title">
      {{ data.title }}
    </h2>
    <div class="accordion">
      <div class="buttons-sticky">
        <div class="buttons">
          <a v-for="(btn, i) in data.content" :key="i" href="#" :class="{active : i === current }" @click.prevent="set(i)">
            {{ btn.title }}
          </a>
        </div>
      </div>
      <div class="description">
        <!-- eslint-disable vue/no-v-html -->
        <div class="info">
          <p>{{ filtered.desc }}</p>
        </div>
        <!--eslint-enable-->
        <div class="placeholder">
          <img
            :src="require('~/assets/photos/education/' + filtered.img )"
            :alt="filtered.title"
          >
        </div>
      </div>
    </div>
  </content-section>
</template>

<script>
import ContentSection from './ContentSection.vue'
export default {
  name: 'AccordionBlock',
  components: { ContentSection },
  props: {
    data: {
      type: Object,
      default: null
    }
  },
  data () {
    return {
      current: 0
    }
  },
  computed: {
    filtered () {
      return this.data.content[this.current]
    }
  },
  methods: {
    set (i) {
      this.current = i
    }
  }
}
</script>

<style scoped>
h2 {
  margin-bottom: 6rem;
}
.buttons-sticky {
  position: relative;
}
.buttons {
  display: flex;
  flex-direction: column;
  gap: 1em;
  position: sticky;
  top: 2rem;
  bottom: 2rem;
}
.buttons a {
  font-size: 1.4em;
  text-decoration: none;
  color: var(--text-gray);
  padding: 1.1rem 2rem .9rem 2rem;
  border: 0.2rem solid transparent;
  background: var(--theme-color);
  border-radius: 1rem;
  line-height: 1.3;
  white-space: nowrap;
}
.buttons a:hover,
.buttons a.active {
  background: white;
  border-color: var(--theme-color);
}
.buttons a.active {
  color: var(--theme-text-color);
}
.accordion {
  display: grid;
  grid-template-columns: 1fr auto;
  gap: 4rem;
  position: relative;
  /* height: min-content; */
}
.description {
  background: white;
  padding: 3.5rem;
  border-radius: 2.5rem;
  display: grid;
  gap: 2em;
  grid-template-rows: 1fr auto;
}
.accordion .placeholder {
  display: flex;
  position: relative;
  /* justify-content: center; */
  /* align-items: center; */
  overflow: hidden;
  border-radius: 1rem;
  height: min(70vh, 450px);
  /* max-height: min(70vh, 450px); */
}
img {
  object-fit: cover;
  width: 100%;
}
@media (max-width: 750px){
  .accordion {
    grid-template-columns: 1fr;
}
}
</style>
