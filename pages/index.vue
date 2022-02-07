<template>
  <div>
    <slider-full-width :path="slideImg" alt="Слайдшоу на главной" />
    <content-section class="add-space">
      <div class="split">
        <div class="cards">
          <card-color-bg
            v-for="(item, i) in cards"
            :key="i"
            :n="i + 1"
            :title="item.title"
            :desc="item.desc"
            :to="item.to"
          />
        </div>
        <div>
          <h2>О Проекте</h2>
          <p>
            Тьютор для ребёнка с ОВЗ - новая, но уже очень востребованная
            профессия среди помогающих специальностей в России. Тьютор помогает
            особому ребёнку включиться в среду школы или детского сада,
            поддерживает его, объясняет ему правила поведения и общения. Следит
            за тем, чтобы ребёнок осваивал образовательную программу, выполнял
            задания.
          </p>
          <p>
            Создавая эту платформу, мы ставили перед собой следующие задачи:
          </p>
          <ul>
            <li>облегчение поиска и подбора тьюторов для родителей;</li>
            <li>формирование базы квалифицированных тьюторов;</li>
            <li>рост и развитие инклюзивный модели;</li>
            <li>повышение значимости работы тьютора.</li>
          </ul>
          <p>
            Если вы родитель особого ребёнка, если вы тьютор и ищете поддержку,
            если вы хотите помогать детям, став тьютором, если вы просто
            интересуетесь инклюзией - вы обязательно найдёте здесь что-то
            полезное для себя!
          </p>
        </div>
      </div>
    </content-section>
    <team />
  </div>
</template>

<script>
import CardColorBg from '~/components/Cards/CardColorBg.vue'
import ContentSection from '~/components/ContentSection.vue'
import SliderFullWidth from '~/components/SliderFullWidth.vue'
import Team from '~/components/Team.vue'
export default {
  name: 'IndexPage',
  components: { ContentSection, SliderFullWidth, CardColorBg, Team },
  data () {
    return {
      slideImg: 'images/mainSlide.jpg',
      cards: [
        {
          title: 'Нам нужен тьютор',
          desc: 'Поможем подобрать подходящего тьютора для вашего ребёнка',
          to: 'for-parents'
        },
        {
          title: 'Хочу стать тьютором',
          desc: 'Присоединись к нашей базе тьюторов для особых детей',
          to: 'education'
        },
        {
          title: 'Уже работаю тьютором',
          desc: 'Узнай о группах супервизии для тьюторов и курсах по взаимодействию с особыми детьми',
          to: 'supervision'
        }
      ]
    }
  }
}
</script>
<style scoped>
.split {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-gap: 5em;
}
.cards {
  display: grid;
  grid-gap: 3em;
}
</style>
