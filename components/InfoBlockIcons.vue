<template>
  <content-section color="theme">
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
        <p v-for="(p, i) in data.content" :key="i">
          {{ p }}
        </p>
      </div>
      <div v-if="position === 'left'" />
    </div>
    <div class="icons">
      <card-icon icon="1" />
      <connector class="connect" />
      <card-icon icon="2" />
      <connector class="connect up" />
      <card-icon icon="3" />
      <connector class="connect" />
      <card-icon icon="4" />
    </div>
  </content-section>
</template>

<script>
import CardIcon from './Cards/CardIcon.vue'
import ContentSection from './ContentSection.vue'
import Connector from './Svg/Connector.vue'

export default {
  name: 'InfoBlock',
  components: { ContentSection, Connector, CardIcon },
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
.icons {
  display: flex;
  align-items: center;
  position: relative;
  justify-content: center;
  padding-top: var(--section-padding);
}
.connect {
  align-self: flex-start;
  margin: 1.5em -1em;
  height: 25%;
  /* --diff: 4em;
  margin-bottom: var(--diff); */
  z-index: 0;
  /* object-fit: fill; */
  flex-grow: 3;
}
.icons .placeholder {
  z-index: 1;
  flex-grow: 1;
}
.connect.up {
  transform: rotate(180deg);
  align-self: flex-end;
  /* margin-top: var(--diff);
  margin-bottom: unset; */
}
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
</style>
