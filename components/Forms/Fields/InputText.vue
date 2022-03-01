<template>
  <div>
    <label v-if="data.label" :for="data.name">
      {{ data.label }}
    </label>
    <input
      :id="data.name"
      :value="value"
      :type="data.type"
      :placeholder="data.placeholder"
      @input="$emit('input', $event.target.value)"
    >
  </div>
</template>

<script>
export default {
  name: 'InputText',
  props: {
    data: {
      type: Object,
      default: null
    },
    value: {
      type: String,
      default: ''
    }
  }
}
</script>

<style scoped>
input::placeholder {
  color: var(--color-placeholder);
}
input {
  background: var(--color-bg-input);
  border: 1px solid var(--color-border-input);
  font-size: 1.6rem;
  padding: 1.7rem 2rem 1.6rem;
  border-radius: 0.6rem;
  line-height: 1;
  width: 100%;
  box-sizing: border-box;
}
label {
  font-size: 1.4em;
  padding-bottom: 1rem;
  display: inline-block;
}
</style>
