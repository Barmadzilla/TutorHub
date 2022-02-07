<template>
  <nav>
    <NuxtLink to="/">
      <img :src="require('~/assets/images/logo.svg')" alt="Логотип ТьюторХаб">
    </NuxtLink>
    <div class="menu">
      <NuxtLink v-for="item in menu" :key="item.to" :to="item.to" class="item">
        {{ item.name }}
      </NuxtLink>
    </div>
  </nav>
</template>

<script>
export default {
  name: 'NavigationBlock',
  data () {
    return {
      menu: [
        { name: 'О нас', to: 'about' },
        { name: 'Работа', to: 'work' },
        { name: 'Обучение', to: 'education' },
        { name: 'Тьютору', to: 'supervision' }
        // { name: 'Контакты', to: 'contacts' }
      ]
    }
  }
}
</script>

<style scoped>
nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.menu {
  display: flex;
  gap: 2em;
}
.menu .item {
  color: var(--text);
  text-decoration: none;
  font-size: 1.4em;
  /* margin-left: 2em; */
  transition: all 150ms;
}
.item:hover,
.item.active-link {
  color: var(--theme-text-color);

}
</style>
