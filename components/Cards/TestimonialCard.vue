<template>
  <div class="testimonial">
    <h4>{{ name }}</h4>
    <p>{{ text }}</p>
  </div>
</template>

<script>
export default {
  name: 'TestimonialCard',
  props: {
    name: {
      type: String,
      default: 'Кристина'
    },
    text: {
      type: String,
      default: 'На курсе от «Йом-йом» мне удалось получить практические навыки, стать ближе к пониманию поведения особых детей.'
    }
  }
}
</script>

<style scoped>
.testimonial{
  padding: 2rem;
  border-radius: 2rem;
  border: .3rem solid var(--theme-color);
}
p{
  font-size: 1.4rem;
}
h4{
  font-size: 1.6rem;
}
</style>
