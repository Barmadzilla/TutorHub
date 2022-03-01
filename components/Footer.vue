<template>
  <content-section :color="'gray'" :type="'footer'">
    <div class="content">
      <div class="sponsors">
        <img
          v-for="logo in sponsors"
          :key="logo.img"
          :src="require('~/assets/images/sponsors/' + logo.img)"
          :alt="logo.alt"
        >
      </div>
      <div>
        <p>
          {{ description }}
        </p>
      </div>
    </div>
  </content-section>
</template>

<script>
import ContentSection from './ContentSection.vue'
export default {
  name: 'FooterBlock',
  components: { ContentSection },
  data () {
    return {
      sponsors: [
        { img: 'eu_flag.png', alt: 'Европейский союз' },
        { img: 'impact_hub.png', alt: 'ImpactHub Москва' },
        { img: 'rosbank.png', alt: 'Росбанк' }
      ],
      description:
        'Платформа создана при поддержке гранта InclusivityLab. Сайт подготовлен при финансовой поддержке Европейского Союза. Содержание сайта является предметом ответственности инклюзивного центра «Йом-йом» и не отражает точку зрения Европейского Союза.'
    }
  }
}
</script>

<style scoped>
p {
  color: var(--text-light);
  font-size: 1.2em;
}
.sponsors {
  display: flex;
  gap: 1.5em;
}
.content {
  display: grid;
  grid-template-columns: 1fr 2fr;
  grid-gap: 5em;
  align-items: center;
}
@media (max-width: 1024px) {
  img {
    height: 4rem;
  }
  p {
    font-size: 1em;
  }
}
@media (max-width: 750px){
  .content {
     grid-template-columns: 1fr;
  }
  .sponsors{
    justify-content: space-between;
  }
  img {
    height: 4.5rem;
  }
}
</style>
