<template>
  <content-section :color="'gray'">
    <div class="scroll">
      <div class="team">
        <team-mate v-for="(teammate, i) in team" :key="i" :data="teammate" />
      </div>
    </div>
  </content-section>
</template>

<script>
import ContentSection from './ContentSection.vue'
import TeamMate from './TeamMate.vue'
export default {
  name: 'TeamBlock',
  components: { ContentSection, TeamMate },
  data () {
    return {
      team: [
        {
          name: 'Яна Иванова',
          desc: 'Директор инклюзивного центра «Йом-йом»',
          photo: 'YanaIvanova.jpg'
        },
        {
          name: 'Мара Гутшабаш',
          desc: 'Создатель платформы ТьюторХаб, программный директор',
          photo: 'MaraGutshabash.jpg'
        },
        {
          name: 'Аксинья Воронова',
          desc: 'Создатель платформы ТьюторХаб, администратор',
          photo: 'AksinyaVoronova.jpg'
        },
        {
          name: 'Даша Бурякова',
          desc: 'специалист по инклюзии',
          photo: 'DashaBuryakova.jpg'
        },
        {
          name: 'Лиза Кнохинова',
          desc: 'специалист по инклюзии',
          photo: 'ElizabethKnokhinova.jpg'
        },
        {
          name: 'Аня Гинзбург',
          desc: 'специалист по инклюзии',
          photo: 'AnyaGinzburg.jpg'
        }
      ]
    }
  }
}
</script>

<style>
.scroll {
  overflow-x: auto;
  position: relative;
  /* scroll-padding-left: 5rem; */
  /* scroll-margin: 50px 0 0 50px; */
  /* scroll-padding-block: 50em; */
}
.team {
  display: flex;
  width: max-content;
  grid-area: 3em;
  align-items: flex-start;
  scroll-padding-block: 50em;
  scroll-snap-type: both mandatory;
}
</style>
