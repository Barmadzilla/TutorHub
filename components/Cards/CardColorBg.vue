<template>
  <nuxt-link :to="to">
    <div class="card" :data-bg="n">
      <h2>{{ title }}</h2>
      <p>{{ desc }}</p>
    </div>
  </nuxt-link>
</template>

<script>
export default {
  name: 'CardColorBg',
  props: {
    title: {
      type: String,
      default: 'Untitled card'
    },
    desc: {
      type: String,
      default: 'Описание карточки'
    },
    n: {
      type: Number,
      default: 0
    },
    to: {
      type: String,
      default: '#'
    }
  }
}
</script>

<style scoped>
a{
  text-decoration: none;
  color: unset;
}
.card {
  background: lightblue;
  border-radius: 2em;
  padding: 3em;
}
.card[data-bg='1'] {
  background: var(--bg-first);
}
.card[data-bg='2'] {
  background: var(--bg-second);
}
.card[data-bg='3'] {
  background: var(--bg-third);
}
</style>
