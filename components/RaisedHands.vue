<template>
  <content-section>
    <div class="content">
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
h2 {
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
img {
  z-index: 1;
}
.content {
  display: flex;
  justify-content: flex-start;
  flex-direction: column;
  align-items: center;
  max-width: 60vw;
  box-sizing: border-box;
  margin: 0 auto;
}
li {
  font-size: 1.5em;
}
@media (max-width: 1024px) {
  img{width: 60vw;}
}
@media (max-width: 480px) {
  img{width: 80vw;}
  .content{
    width: 90%;
    max-width: unset;
  }
  .hands {
    margin-top: -3rem;
  }
}
</style>
