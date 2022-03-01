<template>
  <content-section>
    <div :class="['content', position]">
      <div v-if="position" class="images">
        <card-icon icon="0" class="icon" />
        <card-icon icon="1" class="icon" />
        <card-icon icon="4" class="icon" />
      </div>
      <div class="info">
        <h2>{{ data.title }}</h2>
        <p v-for="(p, i) in data.content" :key="i">
          {{ p }}
        </p>
      </div>
      <div v-if="!position" class="images">
        <card-icon icon="0" class="icon" />
        <card-icon icon="1" class="icon" />
        <card-icon icon="4" class="icon" />
      </div>
    </div>
  </content-section>
</template>

<script>
import CardIcon from './Cards/CardIcon.vue'
import ContentSection from './ContentSection.vue'

export default {
  name: 'InfoBlockImg',
  components: { ContentSection, CardIcon },
  props: {
    data: {
      type: Object,
      default: null
    },
    position: {
      type: String,
      default: null
    }
  },
  data () {
    return {
      test: '--bg-second'
    }
  }

}
</script>

<style scoped>
.content{
  display: grid;
  grid-template-columns: 4fr 2fr;
  grid-gap: 5em;
}
.info {
  place-self: center;
}
.images{
  position: relative;
  padding: 2em 4em;
  display: flex;
  flex-direction: column;
}
.icon{
  margin: -1.5em 0;
}
.icon:nth-child(even){
  align-self: flex-end;
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
</style>
