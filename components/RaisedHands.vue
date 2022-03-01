<template>
  <content-section>
    <div class="container">
      <img :src="require('~/assets/images/raisedHands.jpg')" alt="Hands">
      <div class="hands">
        <h2>
          {{ data.title }}
        </h2>
        <ul>
          <li v-for="(item, i) in data.content" :key="i">
            {{ item }}
          </li>
        </ul>
      </div>
    </div>
  </content-section>
</template>

<script>
import ContentSection from './ContentSection.vue'
export default {
  name: 'RaisedHands',
  components: { ContentSection },
  props: {
    data: {
      type: Object,
      default: null
    }
  }
}
</script>
<style scoped>
h2{
  padding-bottom: 0;
}
.hands {
  border: 0.3rem solid var(--theme-color);
  padding: 3rem;
  border-radius: 2rem;
  margin-top: -5rem;
  z-index: 2;
  background: white;
}
img{
  z-index: 1;
}
.container{
  display: flex;
  justify-content: flex-start;
  flex-direction: column;
  align-items: center;
  max-width: 60vw;
}
li{
  font-size: 1.5em;
}
</style>
