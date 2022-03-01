<template>
  <content-section>
    <div>
      <div class="page nav">
        <ul>
          <li v-for="(item, i) in nav" :key="i">
            <nuxt-link :to="'#' + item.link">
              {{ item.title }}
            </nuxt-link>
          </li>
        </ul>
        <img :src="require('~/assets/images/' + img)">
      </div>
      <div class="title">
        <h1>{{ title }}</h1>
        <div v-if="action.to">
          <button-main :to="action.to" :title="action.name" />
        </div>
        <div v-if="action.href">
          <a :href="action.href" :title="action.name" class="btn">{{ action.name }}</a>
        </div>
      </div>
    </div>
  </content-section>
</template>

<script>
import ButtonMain from './Buttons/ButtonMain.vue'
import ContentSection from './ContentSection.vue'
export default {
  name: 'PageHeader',
  components: { ContentSection, ButtonMain },
  props: {
    img: {
      type: String,
      default: 'pageHeaderImg.jpg'
    },
    title: {
      type: String,
      default: 'Заголовок страницы'
    },
    nav: {
      type: Array,
      default: null
    },
    action: {
      type: Object,
      default: null
    }
  }
}
</script>

<style scoped>
.title {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 2em 2.5em;
  border-radius: 2em;
  background: var(--theme-color);
  z-index: 1;
  position: relative;
}
.title * {
  margin: 0;
}
.page.nav {
  --m-fix: 2.4em;
  display: grid;
  grid-template-columns: 3fr 2fr;
  position: relative;
  align-items: flex-end;
  margin-bottom: calc(var(--m-fix) * -1);
  z-index: 0;
}
img {
  max-width: 500px;
  width: 100%;
}
ul {
  padding: 0;
  list-style: none;
  margin-bottom: calc(var(--m-fix) + 2em);
}
li {
  display: flex;
  align-items: center;
  gap: 1em;
  font-size: 1.6em;
  margin-top: 1rem;
}
li a {
  font-size: inherit;
  text-decoration: none;
  color: inherit;
  transition: color 400ms;
}
li:hover a {
  color: var(--theme-text-color);
}
li:before {
  content: '';
  display: inline-block;
  border-radius: 0.2rem;
  background: var(--theme-color);
  --size: 1.2rem;
  width: var(--size);
  height: var(--size);
  margin-bottom: 0.4rem;
  transition: margin-right 150ms;
}
li:hover:before {
  margin-right: 0.6rem;
}
</style>
