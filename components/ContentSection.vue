<template>
  <section :class="[color, type]">
    <div class="container">
      <slot />
    </div>
  </section>
</template>

<script>
export default {
  name: 'ContentSection',
  props: {
    color: {
      type: String,
      default: ''
    },
    type: {
      type: String,
      default: ''
    }
  }
}
</script>

<style scoped>
section.gray {
  background: var(--bg-light-gray);
}
section.theme {
  background: var(--theme-block-bg-color);
  padding-bottom: var(--section-padding);
}
</style>
<style>
section{
  padding: var(--section-padding) 0;
}
section:last-child{
  padding-bottom: var(--section-padding);
}
section.header{
  padding: var(--header-padding);
}
section.footer{
  padding: var(--footer-padding);
  margin-top: var(--footer-padding);
}

.container {
  margin: 0 auto;
  width: 100%;
  max-width: 1200px;
  min-width: 1024px;
  padding: 0 var(--container-padding);
}
section.theme.action{
  padding: 4rem 0;
}
@media (max-width:1024px) {
  .container {
  min-width: 750px;
}
}
@media (max-width:480px) {
  .container {
    min-width: unset;
  }
}
</style>
