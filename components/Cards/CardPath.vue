<template>
  <div class="card">
    <div class="step">
      {{ number }}
    </div>
    <div class="connector" />
    <div class="info">
      {{ data }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'PathCard',
  props: {
    data: {
      type: String,
      default: null
    },
    number: {
      type: Number,
      default: null
    }
  }
}
</script>

<style scoped>
.card {
  display: grid;
  justify-items: center;
  width: 25rem;
  grid-template-rows: 1fr 4.5em 10em;
}
.connector {
  width: 1px;
  background: var(--theme-color);
  height: 100%;
  margin: 0 auto;
}
.step {
  display: flex;
  justify-content: center;
  align-items: center;
  background: var(--theme-color);
  color: var(--theme-text-color);
  --size: 6rem;
  height: var(--size);
  width: var(--size);
  font-size: 2.8em;
  border-radius: 50%;
  font-weight: bold;
  line-height: 1;
}
.info {
  background: white;
  border: solid 0.2em var(--theme-color);
  padding: 2rem;
  border-radius: 2rem;
  font-size: 1.4em;
  line-height: 1.4;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  width: 100%;
}
</style>
